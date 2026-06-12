---
title: "Ubuntu does not detect CIR device (Acer 5739g laptop, Winbond device)"
date: 2011-01-07
forum: Multimedia Software
---

### Post by spraitukas on 2011-01-07
Hi everyone!

I'm new to Ubuntuforums  and this is my first post so please be merciful :D
I have Acer Aspire 5739g laptop with dual boot: win7 x64 and Ubuntu 10.10 x64. I am trying to get rid off that win thing so i need ubuntu to be able to do everything that windows can. I got everything working the way i want (sound, video, webcam etc) except one thing - wmc IR remote control. I've been searching the answer for about a week now but no luck. Heres whats happening:

I installed lirc, did all the configuration, ran **irw **in terminal but the remote wasn't working at all. So i checked lists of devices to see if its there. I ran:

**sudo lspci** and got

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce GT 130M] (rev a1)
05:00.0 Network controller: Intel Corporation WiFi Link 5100
09:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
```**sudo lsusb** and got

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 062a:3270 Creative Labs 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 04f2:b110 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 0bc2:2300 Seagate RSS LLC 
Bus 002 Device 003: ID 07ca:a310 AVerMedia Technologies, Inc. 
Bus 002 Device 002: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` I am not sure but i think the receiver is not even in list, am i right?
Windows uses Winbond - Nuvaton driver for it. Remote control model is RC804V-B ( [http://liuxprekes.***********/uploads/5/4/5/3/5453123/5532339_orig.jpg](http://liuxprekes.***********/uploads/5/4/5/3/5453123/5532339_orig.jpg) ) and i know its supported by lirc ( [http://lirc.sourceforge.net/remotes/acer/lircd.conf.Aspire_6530G](http://lirc.sourceforge.net/remotes/acer/lircd.conf.Aspire_6530G) )

Can anyone explain me please how can i get this thing recognised so i could use it with lirc or get it working some other way. 

P.S. I am using ubuntu since 9.04 but didnt get much into it until recently. I am not a total noob but i am not a pro either.

---

### Post by BicyclerBoy on 2011-01-07
I think the IR device is part of the Avermedia tuner card.

This card needs non-free firmware package & kernel support & driver.

Add the linux-firmware & linux-firmware-nonfree packages.

The reboot and run
dmesg
read stdout messages about dvb
dmesg | grep dvb

 This will reveal what to do next...

---

### Post by gordintoronto on 2011-01-07
What are you trying to control from the remote?

You might get better results from MythTV forums, or Googling: avermedia remote linux

---

