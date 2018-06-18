# distributed-artificial-intelligence-system
distributed artificial intelligence system, use to deal with datas distributely

需求：通过多进程方式将twitter数据和smartcare数据处理成机器学习可用样本，这些进程可以运行在局域网内多台终端机上。要求各进程中的任务尽量同时完成

输入：twitter API提供的twitter记录数据，smartcare提供的用户使用twitter记录数据。具体格式参考121数据库中表tweets

输出：机器学习需要的统计向量数据。具体格式参考121数据库中表feature_vector

接口：互联网获取twitter记录，局域网获取smartcare数据记录，生成的统计向量保存在121数据库服务器上

     不同终端之间采用socket方式通信
     
     不同进程之间采用fifo queue方式通信
     
UI：暂不涉及

时间：暂不涉及

错误保护：工作进程出错时，放弃正处理的任务，不保存数据，并通知管理进程

         管理进程收到任务出错通知后，重新安排新的进程进行处理
         
最大内存：每个进程分配2GB内存和一个CPU core

最大存储容量：每台终端不得超过三个进程，每个进程不得使用多线程操作smartcare数据库

系统维护：每个工作进程通过通信接口将运行日志发回管理进程，由管理进程写日志文件

设计冲突：权重软件功能50%，系统健壮性30%，系统性能20%



