# self-driving



## java 相关

> 主要的结构在xmind 里面，这里写一些可能会出现的考点 

### 线程


#### Object.wait/notify(all)

> wait & notify* 是为了线程协作涉及的。wait: 线程挂起；notify: 唤醒。

几个问题：
1. 为什么一定要加synchronized
2. 某个进程调用了 wait，其他线程怎么进入锁执行 notify

monitorenter/monitorexit 按照 jvm 规范实现？说回 wait，处理过程中释放同步锁；某个线程调用 notify唤起这个线程的时候,wait 方法退出前会重新获取
这把锁，才能继续执行；


3. wait为什么会InterruptedException

避免破坏调用某个线程的 interrupt 方法。wait 只是单纯唤醒。


4. 多个线程 wait态，某个线程调 nofify是按顺序的吗？

先进入 wait 的线程会被唤起。类似 for 循环？jvm 实现借助了monitorexit：调用notify的线程在退出其同步块的时候唤醒起最后一个进入wait状态的线程，然后这个线程退出同步块的时候继续唤醒其倒数第二个进入wait状态的线程，依次类推




5. notifyall怎么全唤醒

默认最后进入的会先被唤起来

6. wait 的线程是否影响 load

不影响


