---
title: "Wireless on HP Mini 1030NR"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by Sol1 on 2010-05-25
Hey guys,

I've read about all of the problems with the HP Mini's wireless and the Broadcom drivers, but am still looking for a solution to my problem.  Hoping I can find some help here.  Running 10.04 LTS.

```
lspci -vnn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

I have 2 drivers available to me under restricted hardware:

Broadcom B43 wireless driver
Broadcom STA wireless driver

I can get the B43 to connect and work, but not for more than a minute or so at a time.  I see the following in the kernel log after the wifi adapter is activated:

```

May 25 09:16:18 jon-netbook kernel: [  121.825109] Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
May 25 09:16:18 jon-netbook kernel: [  121.825125] b43-phy0: Controller RESET (DMA error) ...
May 25 09:16:18 jon-netbook kernel: [  122.044148] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 25 09:16:24 jon-netbook kernel: [  127.566143] b43-phy0: Controller restarted
May 25 09:16:24 jon-netbook kernel: [  127.577378] b43-phy0: Controller RESET (DMA error) ...
May 25 09:16:24 jon-netbook kernel: [  127.796682] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 25 09:16:30 jon-netbook kernel: [  133.333043] b43-phy0: Controller restarted
May 25 09:16:30 jon-netbook kernel: [  133.333093] b43-phy0: Controller RESET (DMA error) ...
May 25 09:16:30 jon-netbook kernel: [  133.552336] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 25 09:16:35 jon-netbook kernel: [  139.069058] b43-phy0: Controller restarted
May 25 09:16:35 jon-netbook kernel: [  139.069078] Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
```

Has anybody got this working reliably?  Any tips on where to go next?  :confused:

---

### Post by james.whanger on 2010-05-27
I am having the same problem. When I install bcmwl-kernel-source, it stops building the driver and produces a message that says, "Stopped building module for the current kernel.  The source code for this kernel does not seem to be installed." 

I then tried to download a tar from the broadcom site and compile it myself, but received a Makefile error.  Thus, I'm currently at a loss.  I hope someone has a solution.

---

### Post by Sol1 on 2010-05-28
Thanks for the response, James.

Bumping in the hopes that somebody else can provide some direction...  Pretty please?

---

### Post by cartisdm on 2010-09-08
Is there a solution to this yet? I'm having the same problem...


EDIT:  I found this solution after some more digging.  Worked great for me!

[http://ubuntuforums.org/showthread.php?t=1539883](http://ubuntuforums.org/showthread.php?t=1539883)

---

