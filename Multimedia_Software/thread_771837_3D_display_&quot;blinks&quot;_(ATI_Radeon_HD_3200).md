---
title: "3D display &quot;blinks&quot; (ATI Radeon HD 3200)"
date: 2008-04-28
forum: Multimedia Software
---

### Post by amyhughes on 2008-04-28
When I run a 3D application (Second Life) its window "blinks" once per second. As you look at your screen, blink once per second and you'll know exactly what I'm talking about.

Any clues if this is fixable?

This is with integrated graphics chipset 780G (ATI Radeon HD 3200).

Here's the output of lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
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

---

### Post by amyhughes on 2008-04-28
I solved this by turning off visual effects on my desktop!

---

### Post by kekkonj on 2008-12-30
Thanks!

I got resolved my irritating problem too on my Ubuntu 8.10 following this same method (right click on the desktop -> Change Desktop Background -> the last item on the right, Visual Effects -> None)

My problematic hardware was: 
HP Pavillon dv5 1035 with AMD 64 Turion x2 with ATI Radeon HD3450. I installed the latest ATI's driver from: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

---

### Post by jrabbitb on 2009-04-07
As sad as I was to turn off my new pretty graphics this fixed all my video issues. Trouble with avi's, youtube, music player visualization.

Hardware: HD3650 512MB, chipset 780GX (not using hybrid xfire), Phoenom II x3, 4GB DDR2-800, Ubuntu 8.10 64bit, gnome

(Hooray to taking the dive into linux w/out any connection to win/mac!) 

And for my first post, a big THANKYOU to the community in case I ever forget to say it later :)

---

### Post by MichaelPalin on 2009-04-19
Maybe you wont read this anymore, but by catalyst 9.3 compatibility with composite has improved in these flickering aspects. Theoretically, with a 3870x2 I don't even have support, so I haven't seen it by myself.

---

### Post by sschaper on 2009-06-30
Has this been solved? I got the scrolling white flickering dot, and so I went back to Vista because I don't want to stress the HD 3200 or the inverter.

Is there a fix, and if so, what is it?

---

