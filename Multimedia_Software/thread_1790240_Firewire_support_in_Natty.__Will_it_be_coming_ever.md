---
title: "Firewire support in Natty.  Will it be coming ever?"
date: 2011-06-24
forum: Multimedia Software
---

### Post by openfly on 2011-06-24
So from my reading and analysis... Natty removed raw1394 support as well as broke the loopback module required for Video4Linux.

I am trying to get cature going with a sony dfw-v500 which should be startlingly simple.

Curious when if ever ubuntu will be fixing this?

Should I just roll my own kernel and call it a day?

Has anyone seen a work around here?

I want to get v4l going again.

---

### Post by gppixelworks on 2011-10-05
Have you found a solution yet?

I've just received 10 hours of tape that needs to be digitized and have been unable to get a connection via firewire to a Canon MVX200.

Being as I've no native Windows OS anymore, am in a bit of a spot here.  It would be very disappointing to loose a Ubuntu machine just to install a Windows OS for video capture.

---

### Post by lcman on 2011-10-05
I have full support for firewire on my natty. What does lscpi say? Check out the pic

---

### Post by Eolinwen on 2011-10-05
Not me. And I have tried on 3 Natty. My system recognize my firewire cards but not load the driver. It is the fault to the new kernel driver for firewire called JuJu. 
With Juju, you have nothing to do. You run your camcorder and it is ............working.

You could use for that AV Linux, multimedia distribution based on Debian. The next version AV LInux 6.0 will come soon with the last versions of two big Editor Video projects .: Openshot and Kdenlive.

I opened here a bug kernel ([https://bugs.launchpad.net/bugs/842987](https://bugs.launchpad.net/bugs/842987))about this problem because a lot of people can use the firewire with Natty and I am a bit afraid that will be the same on Oneric. About Marverick, he was having the both and Lucid the old version.

---

### Post by gppixelworks on 2012-02-18
> **lcman said:**
> I have full support for firewire on my natty. What does lscpi say? Check out the pic

I"m showing the same on my machine as well.

The firewire PCI card is seen but doesn't connect to a DV camera.
```

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:06.0 Network controller: Ralink corp. Device 3062
02:07.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
05:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```

](*,)

---

