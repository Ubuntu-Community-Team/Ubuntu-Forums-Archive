---
title: "Ndiswrapper Linksys AE1000"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by dth4h on 2010-09-03
Does anyone know how to get ndiswrapper working with the Linksys AE1000 Wifi USB card?  I installed ndiswrapper and I installed the AE1000 driver with the ndiswrapper gui.  But when I reboot the wifi card still is not recognized.  What am I doing wrong?

Running Ubuntu 10.04 LTS

---

### Post by GrantStoner on 2010-09-19
Don't use ndiswrapper, that's for Windows drivers. Linksys AE1000 has a Linux driver, just not on the disk that came with it. The driver you want is RT3572. When I first got mine I used this thread and it worked like a charm. But you'll have to use the version you download instead of the one in the thread, cause it's a little older. And of course you'll have have different /paths/to/the/.file

Linux driver page for Ralink: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Here's the thread: [http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

---

### Post by MetapostAddict on 2010-10-14
The above links were very helpful to  me.

However, a few days ago my linksys ae1000 stopped working.  Have you guys had similar issues?  I'm assuming it has something to do with 10.10, and that the ralink driver will update soon.

---

### Post by GrantStoner on 2010-10-14
Yeah they probably just haven't updated the driver for 10.10 yet - as the new non-beta version was just released not too long ago. I haven't had any issues on 10.04 though. Glad the links helped. ^_^

---

