---
title: "aumix error: can't find /dev/mixer after upgrade to 11.04 (from 10.04)"
date: 2011-09-08
forum: Multimedia Software
---

### Post by the pearly gates on 2011-09-08
Hi,

I recently upgraded from Xubuntu 10.04 to 11.04 and my aumix program is broken.  When I do "aumix" I receive:

```
aumix:  error opening mixer: No such file or directory
```

After searching some forms, I found out that aumix looks for the mixer device in /dev/, and what do you know, it's not there on my machine anymore.  

Now, the audio is working just fine-- the only reason I want to use aumix is because I want to put it as a keyboard shortcut (my keyboard doesn't have a volume controller, so I have to make one).  If there's an easier way to do this, then that would work. I have no problem telling aumix to peace out.

If not, then is there a way to re-install /dev/mixer so that aumix will find it?

Here's my lspci:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
04:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

```

---

### Post by the pearly gates on 2011-09-08
Actually, I just used "amixer" instead of aumix, everything's cool now:


amixer set Master 4-
amixer set Master 4+
amixer set Master toggle

---

