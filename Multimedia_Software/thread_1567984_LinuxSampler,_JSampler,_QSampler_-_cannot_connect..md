---
title: "LinuxSampler, JSampler, QSampler - cannot connect."
date: 2010-09-04
forum: Multimedia Software
---

### Post by dchurch24 on 2010-09-04
Hi all,

I've been trying to get LinuxSampler up and running, but am failing dismally.

I've had no end of trouble, and am now finally at a position where QSampler and JSampler both allow me to make a midi connection through Jack.

The problem is, that when I load a .gig file I get the following errors:

```

Starting disk thread...Thread: WARNING, can't mlockall() memory!
OK
Thread: WARNING, can't mlockall() memory!
Scheduling '/home/dave/Desktop/Clean_Up/maestro_concert_grand_v2.gig' (Index=0) to be loaded in background (if not loaded yet).
Thread: WARNING, can't mlockall() memory!
Loading gig file '/home/dave/Desktop/Clean_Up/maestro_concert_grand_v2.gig'...linuxsampler: malloc.c:3074: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.

```


and:

```

04-Sep-2010 17:49:35 org.jsampler.CC loadOrchestras
INFO: /home/dave/.jsampler/orchestras.xml (No such file or directory)
java.io.FileNotFoundException: /home/dave/.jsampler/orchestras.xml (No such file or directory)
   at java.io.FileInputStream.open(Native Method)
   at java.io.FileInputStream.<init>(FileInputStream.java:137)
   at java.io.FileInputStream.<init>(FileInputStream.java:96)
   at org.jsampler.CC.loadOrchestras(CC.java:399)
   at org.jsampler.JSampler.initGUI0(JSampler.java:103)
   at org.jsampler.JSampler.access$100(JSampler.java:36)
   at org.jsampler.JSampler$1.run(JSampler.java:92)
   at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
   at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
   at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
   at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
   at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
   at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
   at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
   at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
04-Sep-2010 17:49:37 org.linuxsampler.lscp.Client setSoTimeout
INFO: Unable to set timeout
java.net.SocketException: Socket Closed
   at java.net.AbstractPlainSocketImpl.setOption(AbstractPlainSocketImpl.java:182)
   at java.net.Socket.setSoTimeout(Socket.java:1035)
   at org.linuxsampler.lscp.Client.setSoTimeout(Client.java:188)
   at org.jsampler.task.Global$SetClientReadTimeout.exec(Global.java:265)
   at org.jsampler.task.EnhancedTask.run(EnhancedTask.java:57)
   at net.sf.juife.AbstractTask.invokeAndWait(AbstractTask.java:180)
   at net.sf.juife.TaskQueue.processTheQueue(TaskQueue.java:176)
   at net.sf.juife.TaskQueue.start0(TaskQueue.java:147)
   at net.sf.juife.TaskQueue.access$000(TaskQueue.java:43)
   at net.sf.juife.TaskQueue$1.run(TaskQueue.java:140)

```

It appears that LinuxSampler is refusing the connection for some reason. It's started on 0.0.0.0:8888 (which both the frontends are set to as well). Port 8888 is open when I do a nmap.

I'm lost!

Does anyone know about LinuxSampler that could point me in the right direction please.

I'm running 64bit UbuntuStudio 9.10 (I tried 32 bit 10.04, but couldn't even get jack to start, or my midi keyboard recognised, so I reverted back).

---

### Post by dchurch24 on 2010-09-06
Having struggled with this for a while and getting nowhere, does anyone know of another sampler for linux that handles .gig files that I perhaps might be able to use instead?

---

### Post by cchhrriiss121212 on 2010-09-06
Have you tried using it with ALSA instead of jack?
I'm fairly certain that qsampler is the only Linux project that includes .gig files.

**Edit**: Just found [this page]("http://bb.linuxsampler.org/viewtopic.php?f=6&t=317") that seems to show a solution:
> To make mlockall work, it is often enough to make sure that the current  unix user is a member of the "audio" group. Look after "memlock" in  /etc/security/limits.conf.
So edit your limits.conf needs to have:
@audio - memlock unlimited

Then do: 
```
sudo adduser "yourusername" audio
```

---

### Post by dchurch24 on 2010-09-06
Hi, I made myself a member of that group, but I still get the same error, also I am no longer a sudoer - how can I put myself back as a sudoer?

I also cannot run Jack in realtime mode due to permissions error, so I think this is on the right track.

---

### Post by cchhrriiss121212 on 2010-09-06
[This]("http://www.psychocats.net/ubuntu/sudo") should help you out with sudo. You should stop getting the error once you edit your /etc/security/limits.conf file successfully. In addition to the memlock line you need to add another to let you use realtime.
So once you have sudo back, follow this:
```
sudo gedit /etc/security/limits.conf
```
and paste this:
@audio - rtprio 99
@audio - memlock unlimited

Then you just need to save and reboot for this to take effect.

---

### Post by dchurch24 on 2010-09-06
Hi, thanks for that.

It works!

I still get quite a lot of crashes from LinuxSampler, Rakarrack etc... with memory errors (did a memtest, RAM is fine - it bloody should be, it cost me over £1000!!).

...but it's working ;-)

Thanks so very much for you help, much appreciated!

---

