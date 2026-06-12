---
title: "Strange problem with fglrx on radeon 9200"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by cayco on 2006-10-31
Hi! I am an experienced Linux user but I cannot find solution for my problem. I read zillion of ati binary driver howtos and still nothing. I have no DRI in my X.org (fresh edgy) and my glxinfo says Mesa, bla, bla, bla. I attache my configuration files and listings from lsmod, lspci, etc. Can anyone help me please?

cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : AMD Sempron(tm) Processor 2500+
stepping        : 2
cpu MHz         : 1406.967
cache size      : 256 KB

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)


cheers

Krzysztof Kajkowski

---

### Post by Stemp on 2006-10-31
I think that the ATI 9200 serie is not anymore supported by the fglrx driver.

---

### Post by cayco on 2006-10-31
sory for double posting (connection error)

---

### Post by cayco on 2006-10-31
I've just check it - you are right! 

"As of driver version 8.29.6 support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

Users with these products should use driver version 8.28.8"

take from here:
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176)


BUT, I use driver 8.28.8 which DOES support my card. You can see it in my X.org.log.

anyone any idea why it does not work?

regards

cayco

---

### Post by pstracha on 2006-11-05
I'm having the exact same problem, been working on it all day long too. Anyone have any luck with the 9250 and fglrx v8.28.8? ](*,)

---

### Post by robertwoes on 2006-11-06
same issue. i have ati radeon 9200 SE .. got the 8.28.8 and need help... anybody?

---

### Post by SledgeHammer_999 on 2006-11-06
I had the same problem. Follow this [guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

You need to disable composite as the guide says.

---

### Post by kharl on 2007-02-05
> **SledgeHammer_999 said:**
> I had the same problem. Follow this [guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

You need to disable composite as the guide says.

I followed this guide but I got just black screen (no video signal or out of range, but monitor spec didn't change). 

HW: ATI Radeon 9100 (R200), ViewSonic VP930 LCD 
Driver: ATI 8.28.8
Ubuntu/edgy

---

