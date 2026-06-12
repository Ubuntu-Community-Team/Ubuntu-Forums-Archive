---
title: "Driver install for Wired Ethernet on Abit KV8 Pro (ubuntu 13.04)"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by ZpLiTTeR on 2013-05-28
Hi all.

I confess I am relatively new to the Linux scene, so bear with me. I have an old AMD64 3200+ with 1GB of ram on Abit KV8 Pro that I thought I would set up as a small storage server on LAN. Problem is, the onboard NIC does not work out of the box. I am running Ubuntu 13.04 64-bit version.


Based on this post the chipset is a [COLOR=#000000][FONT=Verdana]VIA VT6122. [/FONT][/COLOR][http://osdir.com/ml/linux.debian.ports.amd64/2004-10/msg00453.html](http://osdir.com/ml/linux.debian.ports.amd64/2004-10/msg00453.html)[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
I found some drivers for older ubuntu versions (10.04 / 10.10) on the VIA linux portal, but i'm not sure how to make those work and if it is even possible.
[http://www.viaarena.com/Driver/velocity_linux_v1.43.zip](http://www.viaarena.com/Driver/velocity_linux_v1.43.zip)

I tried following the instructions in the above zip-file, but I got stuck when it required an updated config-file for the kernel - or something?

Help would be greatly appreciated.

---

### Post by sanderj on 2013-05-28
What is the output of:
```

lspci -nnk | grep -i -A2 net

```

---

### Post by ZpLiTTeR on 2013-05-28
Thank you for responding so quickly.

I'm not sure if I am doing something wrong, but running that command in terminal returns nothing - not even an error prompt. In case it might be helpful, running lspci returns:

00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)


Thanks again.

---

### Post by sanderj on 2013-05-28
That's weird: there is no network interface at all. (That explains why you get no output with the full command).

I would go into the BIOS and check whether you can enable the onboard ethernet device.

And you could post the output of "lsusb", but I don't expect your NIC to be connected via USB.

---

### Post by ZpLiTTeR on 2013-05-28
I just checked the bios. Onboard LAN is enabled. I tried disabling and re-enabling. Then I tried fail-safe defaults - to no avail.


I changed the RJ-45 from the PC to the switch (as well as changed to another port on the switch) - still nothing.


lsusb output:


Bus 002 Device 002: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by sanderj on 2013-05-28
Then I'm out of ideas; if it's not in lcpci (nor lsusb), Linux cannot see it.

I would install a 5 Euro NIC into your system.

---

### Post by ZpLiTTeR on 2013-05-28
Okay. Cheers. Do you have any recommendations?

I have two old cards laying around I could drop into PCI. Which one would you reckon works the best?

TOPCOM Lan card 115 - Realtek (RTL8139D)

3Com 10/100BASE-TX Ethernet Adapter (Not sure of chipset - it says "Parallel tasking II - Performance" on one of the chips).

I guess if there's a "known to work"-list for Ubuntu 13.04 I could just follow that?

---

### Post by sanderj on 2013-05-28
Both will probably work. I would go for the Realtek ... just because I like Realtek as all their hardware worked for me out-of-the-box under Linux

---

### Post by ZpLiTTeR on 2013-05-28
[SUP]Added the Realtek based card. Entered BIOS and disabled onboard LAN (just to be sure they wouldn't conflict). Booted the PC and lo and behold - I am now typing replying from the PC in question. While not technically a solution to the onboard LAN not working, the outcome was still working ethernet connection.

Thank you for the help, much appreciated.

Chris
[/SUP]

---

### Post by sanderj on 2013-05-28
Cool. And what's now the output of:

```
lspci -nnk | grep -i -A2 net
```

---

### Post by ZpLiTTeR on 2013-05-28
Terminal Output for "lspci -nnk | grep -i -A2 net":

00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
	Kernel driver in use: 8139too

Thanks again.

---

