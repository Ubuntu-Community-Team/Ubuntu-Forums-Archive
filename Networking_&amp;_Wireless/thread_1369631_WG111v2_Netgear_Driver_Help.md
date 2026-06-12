---
title: "WG111v2 Netgear Driver Help"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by aquamorph on 2010-01-01
I have been trying to install my Netgear WG111v2 Driver on my Ubuntu 9.4 computer but everything I have tried has failed. I have looked online and found instruction but it did not work. I would appreciate some help.

---

### Post by prshah on 2010-01-01
> **aquamorph said:**
> install my Netgear WG111v2 Driver on my Ubuntu 9.4 computer

I find that the WG111 usb wireless works natively using the rtl8187 <?> driver; however I cannot recall if I've used v2 or v3. If you can find wireless networks, then your driver is OK. If no wireless card is recognized at all, then maybe you will have to use ndiswrapper as outlined below.

Please see this thread: [[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless ]("http://ubuntuforums.org/showthread.php?t=756260") for a step-by-step command line guide, with expected outputs.

Please post back here if you have troubles, with specifics of command and output.

---

