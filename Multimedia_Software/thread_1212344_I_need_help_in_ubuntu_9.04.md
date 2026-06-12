---
title: "I need help in ubuntu 9.04"
date: 2009-07-13
forum: Multimedia Software
---

### Post by dbowler on 2009-07-13
I downloaded xorg-edit. It says to extract the file to the home directory. I did that. Then it says to change directory in the readme file. I did it in terminal and it says no such file or directory. I also need help with wine. I have the 1.01 version. It works fine, but i cant get my ten pin championship bowling pro to work. Do i have to configure the xorg.conf file for my graphics card. I have a ati radeon 320m card and my vga driver is ati radeon mobility u1, and i went to lspci in terminal and it shows this. What do i do to configure my graphics card.

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
Please help me!

---

### Post by dbowler on 2009-07-13
I have an ati radeon 320m and my vga is ati radeon mobility u1. How do i configure them in xorg.conf. I have a bowling game called ten pin championship bowling pro. When i play the game it lags. Should i configure xorg.conf with the vesa driver. Please help me! I dont know what to do.

---

### Post by overdrank on 2009-07-13
> **dbowler said:**
> I have an ati radeon 320m and my vga is ati radeon mobility u1. How do i configure them in xorg.conf. I have a bowling game called ten pin championship bowling pro. When i play the game it lags. Should i configure xorg.conf with the vesa driver. Please help me! I dont know what to do.

Hi and welcome, that ATI graphics is pretty old and the driver that comes with Jaunty 9.04 would probably work the best.
If it is possible to adjust the memory shared with the ati graphics in bios this may help. If not you may use the xfix option when booting into recovery mode which is usually the second choice when booting from the grub.
Please do not create multiple threads on the same issue. Threads merged :)

---

