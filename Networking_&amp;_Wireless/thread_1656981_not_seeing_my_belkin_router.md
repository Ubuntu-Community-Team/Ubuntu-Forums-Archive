---
title: "not seeing my belkin router"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by aaron1011 on 2010-12-31
hello, could use some help

i am using a belkin N router with a belkin N usb wireless card

results for    lsusb

050d:8053

results for     iwconfig

lo             no wireless extensions

eth0           no wireless extensions

eth1           no wireless extensions




where do i go from here?

thanks

---

### Post by khelben1979 on 2010-12-31
I think your solution is with the [NDISwrapper]("http://en.wikipedia.org/wiki/Ndiswrapper").

There was a discussion [here]("http://ubuntuforums.org/showthread.php?t=863591") where they discussed how this looks like, and what's important from that discussion is that they mention to activate the kernel module by using the **modprobe** command, then once that is done, a Windows driver for your network card can (hopefully!) be used by your Ubuntu system.

If the driver was provided with the Linux kernel, it can be loaded with the modprobe command and then it would be used automatically by the system, but I don't know if it's supported. Normally you'll find supported platforms regarding your hardware by the manufacturers website, such as Belkin in this case. Have you checked that up if it's officially supported?

---

