---
title: "fresh installation of ubuntu 12.04 with no wifi"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by fidel2 on 2013-08-28
Hi..

Just installed ubuntu 12.04 and I dont have any wifi, after I choose the OS in GRUB I get the following message:

[11.853845] rtlwifi: firmware rtlwifi/rtl8188efw.bin not available

this is what I get when I run iwconfig:
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

this is lspci

```
axl456@axl456-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)


```

---

### Post by bkline on 2013-08-28
Might not be the problem, but just in case: if this is a laptop, check to make sure you haven't inadvertently nudged the wi-fi on/off switch into the off position while moving the machine.  This has happened to me more than once, and it's a real head-scratcher until you realize what you've done.

---

### Post by grahammechanical on 2013-08-28
In 12.04 you will find Additional Drivers utility in the Dash. It might even be announcing itself in the top panel. We usually use Additional Drivers to activate proprietary video drivers but I think it can also offer us a wireless driver.

Also run
```
rfkill list
```

That will tell you if the wireless LAN is blocked in software or in hardware.

Regards.

---

### Post by fidel2 on 2013-08-28
@bkline, yes is a laptop but it doesnt have a switch for the wifi, is a button but it wont work if I press it..

@grahammechanical the additional drivers utility doesnt show anything related to wireless, its actually showing some propietary graphic drivers from amd. 

when I run rfkill list it doesnt show anything..

---

