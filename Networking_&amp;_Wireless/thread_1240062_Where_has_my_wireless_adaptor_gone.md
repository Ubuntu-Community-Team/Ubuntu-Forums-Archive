---
title: "Where has my wireless adaptor gone?"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Twizzle on 2009-08-14
I have a Samsung NC10 and have been running Ubuntu 9.04 on it for the last month or so. Everything has worked fine and I followed [this]("http://www.voria.org/forum/showthread.php?tid=41&page=1") thread to get it all running.

Today, I brought the computer our of standby and it would not connect to the wireless network. It could see mine and my neighbours but would not connect. I rebooted and when I logged back in, there was no network at all. The network icon on the taskbar just shows the wired network (which I have now plugged in and works)

I have tried 
```
lspci | grep Network
```

but get nothing. My output from 
```
lspci
```

is

```
john@laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Class ffff: Device 0001:0200 (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

```

It looks like my wireless adaptor has vanished. The netbook is only a few months old so I guess I could take it back (although I am sure they will complain that Windows is not still installed so I would have to go through the palava of reinstalling it!)

Can any one suggest a way that I can find out if my network adaptor has died or if Ubuntu just will not see it any more.

I even tried booting into the previous kernel to check it was not that .

---

### Post by superprash2003 on 2009-08-14
post output of **lshw -C network** from the terminal

---

