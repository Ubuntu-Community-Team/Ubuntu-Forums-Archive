---
title: "Slow socket sends with ported app on Ubuntu 9.10 LiveCD"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by ChrisCphDK on 2009-11-12
Hi.

I've ported an application I made on Mac OS X, which uses BSD sockets to send HTTP POST request.

I'm not sure if it's a network problem, or some other issue with the hardware, so please excuse me if this is the wrong section, and point me to a better suited one.

When booting up Karmic Koala liveCD, and running the application, the application runs, but it is very slow: from debug output I can see that it calls the send function to send the data, but then it sits for almost a second or two, before completing.
Needless to say, it runs at "normal" speed on Mac OS X.
The code uses PThreads, and otherwise uses POSIX C++ code.

I've tried using the ethtool to set the linkspeed to the various available settings, with no improvement.

Here's some system information, let me know if any specifics are needed:

Laptop: 
Lenovo ThinkPad R400
Memory: 2 GB (reports 1.9 GB)
CPU: Intel Core2 Duo (T5870)

Ubuntu: 
Ubuntu 9.10 (karmic)
Kernel: Linux 2.6.31-14-generic
Gnome 2.28.1

Any hints will be appreciated.

Best regards,
Chris

---

### Post by dvlchd3 on 2009-11-12
Is it because you are running on the LiveCD?  (Which is going to run much slower than if Ubuntu was installed on your HDD)  Have you tried running the application on an Ubuntu Installation?

---

### Post by ChrisCphDK on 2009-11-12
dvlchd3, I haven't tried running it on an installed version of karmic. 

Is it incorrect to assume that it should run the same, whether in an installed ubuntu or livecd, with the specified hardware?

There is plenty of free RAM, CPU and no CDROM activity, while executing the application.

The objective is that the application will be used during an exam where it will be demonstrated that it can run on various UNIX flavors (using different liveCDs). I'd hate to have to start creating partitions/slices and installing all of different liveCDs (Frenzy, Karmic, FreeSBIE, Debian Live, Knoppix etc.). 

Best regards,
Chris

---

