---
title: "DWA-125 for Backtrack 5 R2"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by Arcarna on 2012-02-29
I just purchased this adapter for my laptop and have been through most articles on here and elsewhere and have not gotten it to work yet. I am not new to Linux and have never had this much trouble before. Also, I know this may sound like a lot but if at all possible I need this to work by Friday morning. Any help... please lead the way.

---

### Post by enjoijesus94 on 2012-02-29
Hello 

Im no expert on linux 
but i can help

what is the problems with your adapter friend ?

im using blackbuntu instead of backtrack for certian reasons.

but what are the problems ?:confused:

---

### Post by Arcarna on 2012-02-29
The adapter doesn't show in ifconfig or anything and compiling the drivers proved to be a task that I am unequipped for as I kept coming across files that were not there and then having to fix that and so on. Never actually made it all the way. Got to make install and it broke because there is no rt2780sta.ko file.

---

### Post by enjoijesus94 on 2012-02-29
Hmmm did you check your drivers website for the right driver and install it via terminal?

because i had a similar problem with a NVIDIA graphics card 

it kept breaking and was a hassle until i went to the website downloaded the driver and installed through GDM

try to go on the website and look for your driver and ill guide you through the installation man

---

### Post by Arcarna on 2012-02-29
D-Link themselves does not have a Linux driver. Most of the guides have used the chipset drivers instead. Though there was mention of using the driver from the disc...unfortunately there was no guide for that and I don't know which to use. I have the drivers for the chipset already though.

---

### Post by enjoijesus94 on 2012-02-29
Hmmmm ok.

will it even read when you post this command inside terminal?

```
lspci
```

---

### Post by Arcarna on 2012-02-29
lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller (rev 10)


Doesn't appear that way.

---

### Post by enjoijesus94 on 2012-02-29
I see hmmm ok i got something check this post to see if your card or adapter is supported.

[[COLOR=RoyalBlue]_http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink_[/COLOR]]("http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")

hoping it is man

---

### Post by Arcarna on 2012-02-29
It says it is supported but that it's flaky... But it works fine in Ubuntu 12.04 LTS.

---

### Post by enjoijesus94 on 2012-02-29
Sorry about the wait 

check this out 
and see if you have any luck 

[http://ubuntuforums.org/showthread.php?t=1625657&page=15](http://ubuntuforums.org/showthread.php?t=1625657&page=15)

even tho your running on backtrack5 R2
your using a gnome interface.

report back if this helps :popcorn:

---

### Post by Arcarna on 2012-02-29
So I ran through that and it shows up in iwconfig but states that there is no module and that it doesn't support scanning.

---

### Post by Arcarna on 2012-02-29
Going to try rolling back to Backtrack 5 before all the kernel updates and such and I will post after doing such.

---

### Post by enjoijesus94 on 2012-02-29
ok report it and we will see what we can do

---

### Post by chili555 on 2012-02-29
> **Arcarna said:**
> Going to try rolling back to Backtrack 5 before all the kernel updates and such and I will post after doing such.I'll be glad to help. Please post:```
lspci -nn | grep 0280
lsmod | grep 819
rfkill list all
```Thanks.

---

