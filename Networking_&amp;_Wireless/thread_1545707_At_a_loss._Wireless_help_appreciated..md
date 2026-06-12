---
title: "At a loss. Wireless help appreciated."
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by personsunknown on 2010-08-04
First let me say that it has been a very long time since I have experimented with any Linux Distro so I did not know where exactly to post this as I am a beginner....again.

I am trying to get my wireless up and running on an old Dell Latitude | D610 using ubuntu netbook remix. I am using a writable USB boot. Ethernet works fine. I should also note that there is a dead HD in the  laptop that had Windows Vista installed on it.

I followed some of the advice on [http://ubuntuforums.org/showthread.php?t=1529940&page=2](http://ubuntuforums.org/showthread.php?t=1529940&page=2) and was able to get my card? recognized and installed some flash then rebooted to see if the wireless would stick. It did not. 

lspci results

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```):P

---

### Post by rlzyoner on 2010-08-04
I usually follow this guide and things always work out

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by personsunknown on 2010-08-05
> **rlzyoner said:**
> I usually follow this guide and things always work out

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
Thanks for the link. I am afraid that I am still at a loss. This says that my Chip type is compatible yet I am making no progress due to installation? errors.

I should also mention that my wireless light/indicator was on constantly before and now it will not turn on at all.

EDIT: sudo modprobe b43 turned on my wireless. Am I going to have to type this everytime I want to connect?

---

