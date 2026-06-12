---
title: "WMP300n Kernel Module Name BackTrack3"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by stretch427 on 2009-01-05
Looking for some help with BackTrack3, not sure if this is the right place. My problem is finding the Kernel Module name for my PCI wireless card (Linksys WMP300n Wireless Adapter).

Has anyone tried BT3 with this card? If so how did you do it?

If not, any Idea's on how I might go about finding the kernel module?

 Any help would be awesome! Thanks.

Stretch

---

### Post by stretch427 on 2009-01-05
Bump

---

### Post by Ayuthia on 2009-01-05
Have you checked lspci -nn to see what the chipset is?

---

### Post by stretch427 on 2009-01-06
Here is the output of that command and the Wifi Controller is at the bottom: 

00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IB (ICH9) LPC Interface Controller [8086:2918] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller [8086:2921] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0611] (rev a2)
03:00.0 IDE interface [0101]: JMicron Technologies, Inc. JMB368 IDE controller [197b:2368]
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 13)
05:03.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

How do the chipset and the "modulename" correspond? In BT3 I need to know module name for modprobe command right?
Ideas?

---

### Post by Ayuthia on 2009-01-06
> **stretch427 said:**
> 
05:03.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

How do the chipset and the "modulename" correspond? In BT3 I need to know module name for modprobe command right?
Ideas?
This is your wireless card.  This means that you have a Broadcom chipset and it most likely has wireless-n and is not supported by the b43 driver at this time.  Your options right now is to use the wl driver or ndiswrapper.

I am not for sure if the wl module will work on BT3 or not.  I have not tried compiling it on there yet.  The module came out in July and has been compiled in 2.6.24 and higher, but I have seen or tried to compile it on anything older.

---

### Post by Ayuthia on 2009-01-06
> **stretch427 said:**
> 
05:03.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

How do the chipset and the "modulename" correspond? In BT3 I need to know module name for modprobe command right?
Ideas?
This is your wireless card.  This means that you have a Broadcom chipset and it most likely has wireless-n and is not supported by the b43 driver at this time.  Your options right now is to use the wl driver or ndiswrapper.

I am not for sure if the wl module will work on BT3 or not.  I have not tried compiling it on there yet.  The module came out in July and has been compiled in 2.6.24 and higher, but I have seen or tried to compile it on anything older.

---

### Post by stretch427 on 2009-01-06
I well it works fine in Ubuntu, and I have the restricted drivers going and stuff. But your saying BT3 can't support it at this time, and I wasn't quite sure about using ndiswrapper to insall, should I just wait until someone compiles it or should I try using ndiswrapper?

---

### Post by Ayuthia on 2009-01-06
I am saying that BT3 is using an older kernel so I am not for sure that the wl driver compiles there. I am not for sure about how to run updates in BT3 because I have only used it as a liveCD not as a normal install so the driver may even be available.

You can try to compile the driver yourself:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Another option to try is also using [nubuntu]("http://www.nubuntu.org/") which is similar to BackTrack3 but is based on Ubuntu.

---

