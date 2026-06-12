---
title: "Slow Download speed"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Neko_Master on 2009-02-15
Ok so Im having an ok time with ubuntu except for the fact that downloading anything is going at a near snails pace (at least for me) :(:(:(

Normally, in Windows XP my downloads max out at 400KBps (it should 800KBps but BELL Canada likes to f*** around and not gimme my speed)

But when im in ubuntu it doesnt go anyhigher then 70KBps when downloading from firefox, Updater, Synaptic Package Manager and Terminal (using the apt-get xxxx commands) :(

Im using a Realtek Gigabit Ethernet (Onboard) with Ubuntu 8.10, It was faster before when I downloaded though a virtual Machine (using the same NIC) Is there anyway to fix this? :confused:

---

### Post by Philo1 on 2009-02-15
You may have already done this as it seems that your looking at a poss software issue. However have you looked at your hops and or the servers your hitting? It seems more plausible to look at your NIC (hardware) or your outside stats. I wouldn't lean toward it being a issue with 8.10. Are you on a hard line of wifi?

---

### Post by Neko_Master on 2009-02-15
> **Philo1 said:**
> You may have already done this as it seems that your looking at a poss software issue. However have you looked at your hops and or the servers your hitting?

Poss? HOPS? WTF? IDK wat those are, and Im dl'ing from servers I konw that have higher upload speeds, like I said, I got higher speeds on a virtual machine then running Linux directly.

---

### Post by AlexBellisBrown on 2009-02-15
We need to be sure of your Ethernet card, can you go to terminal and post here the output of:

lspci

and

lsusb

---

### Post by Philo1 on 2009-02-15
> **Neko_Master said:**
> Poss? HOPS? WTF? IDK wat those are, and Im dl'ing from servers I konw that have higher upload speeds, like I said, I got higher speeds on a virtual machine then running Linux directly.

Poss - Possible (abb) -- I was merely suggesting that you trace your hops from point to point. If you go to system tools > Network tools -- you can perform some _basic_ troubleshooting. Otherwise you can use the terminal --(CLI)-- to do this if you wish. My experiences almost point toward a crappy ISP. The tech's often have no clue as to what any of the jargon is or how the network itself works. Let me know what you find out. It makes sense that your speed may be faster running a virtual setup for that simple fact of what it is. I'll be glad to help out if I can, just see if you can't gather some data so it can be analyzed.

---

### Post by Neko_Master on 2009-02-15
> **AlexBellisBrown said:**
> We need to be sure of your Ethernet card, can you go to terminal and post here the output of:

lspci

and

lsusb

Ok heres the info

lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

lsusb

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 12f7:1a03 Memorex Products, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 03f0:5511 Hewlett-Packard Deskjet F300 series
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

