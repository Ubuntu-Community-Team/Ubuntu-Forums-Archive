---
title: "Dell Inspiron 580 no network problem"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by polnessan on 2010-02-18
Just purchased a Dell Inspiron 580 MT tower pc with Windows Professional.
However unable to connect to the network or the internet when I load a copy of Ubuntu Karmic on dual boot. Windows networking and internet working fine.
Is this an ethernet adaptor hardware issue?
Broadcom NetXtreme 10/100/1000 Gigabit Ethernet controller-PCI Express card
Will try later connecting through a usb ethernet adaptor to see if this is really the problem.
Any comments appreciated

---

### Post by brentonk on 2010-02-19
I had the same problem with the same computer: a new Dell Inspiron 580 that wouldn't connect to the Internet running Ubuntu 9.10. (In addition to the network problems, it was also freezing, which I fixed by running it in safe graphics mode.)

The issue seems to be that the Broadcom driver fails to support the wireless card, which appears to have been fixed in more recent kernel releases. When I run a live CD of Ubuntu 10.04a2, which has the 6.32 kernel, the network problems go away immediately. (I still get freezing if I don't run in safe graphics mode, but that's a different story...)

---

### Post by polnessan on 2010-02-19
Yes!
Have just tried a live cd copy of Ubuntu 10.04a2 Lucid Lynx and the network is fine.
No problems with the graphics, so I will run with this version.
Your help appreciated.

---

