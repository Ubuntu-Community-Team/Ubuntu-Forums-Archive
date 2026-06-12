---
title: "Nvidia 6200 AGP graphics Card Ubuntu - Crash"
date: 2009-09-16
forum: Multimedia Software
---

### Post by Hemal on 2009-09-16
Hey People,

My Nvidia 6200 AGP graphics card crashes (the whole pc, I can't remotely ssh into it..!) when used with Nvidia drivers!

I have ASUS p5vdc-mx motherboard.

I have tried to use the Hardware Drivers section of Ubuntu to install the nvidia driver and still crashes.

I have used the nvidia driver from nvidia site and that crashed as well.

I have completely uninstalled the nvidia driver using following and then re-installing it and still crashed :(

  apt-get purge nvidia-glx*

I have used the following apt command to install the driver:

  apt-get install nvidia-glx-180

I used the ppa xorg edgers and still no go:

[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

I will put the Xorg logs and syslog when I get home.

I am curious if anyone else has run in to problems with this card and any suggestions.

Also, after installing the driver, I would do nvidia-xconfig to get the Xorg to recognise the nvidia driver.  Then after that rebooting, crashes the whole system.  

The only way to get back is to hard reboot and then use the recovery method and then doing the dpkg-reconfigure -phigh xserver-xorg.

---

### Post by Hemal on 2009-09-16
Some debugging info:

> dmesg | grep nvidia

[   15.546817] nvidia: module license 'NVIDIA' taints kernel.
[   15.802330] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

> lsmod | grep nvidia

nvidia               9550436  0
agpgart                42696  2 nvidia,via_agp


Syslog entries:
Sep 16 07:13:12 hemal-desktop kernel: [   10.429552] udev: starting version 141
Sep 16 07:13:12 hemal-desktop kernel: [   11.161135] parport_pc 00:07: reported by Plug and Play ACPI
Sep 16 07:13:12 hemal-desktop kernel: [   11.161201] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Sep 16 07:13:12 hemal-desktop kernel: [   11.453590] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 16 07:13:12 hemal-desktop kernel: [   11.468584] input: PC Speaker as /devices/platform/pcspkr/input/input8
Sep 16 07:13:12 hemal-desktop kernel: [   11.497748] ppdev: user-space parallel port driver
Sep 16 07:13:12 hemal-desktop kernel: [   11.510580] Linux agpgart interface v0.103
Sep 16 07:13:12 hemal-desktop kernel: [   11.646557] agpgart: Detected VIA VT3314 chipset
Sep 16 07:13:12 hemal-desktop kernel: [   11.670807] agpgart-via 0000:00:00.0: AGP aperture is 512M @ 0xc0000000
Sep 16 07:13:12 hemal-desktop kernel: [   11.945339] nvidia: module license 'NVIDIA' taints kernel.
Sep 16 07:13:12 hemal-desktop kernel: [   12.200860] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 16 07:13:12 hemal-desktop kernel: [   12.201791] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009
Sep 16 07:13:12 hemal-desktop kernel: [   12.236406] Linux video capture interface: v2.00
Sep 16 07:13:12 hemal-desktop kernel: [   12.351796] saa7130/34: v4l2 driver version 0.2.14 loaded

---

### Post by Hemal on 2009-09-19
Ok, so I switched to jaunty 64 bit.

Used envy to uninstall any kernel modules.

Then downloaded the 185.160 nvidia driver from the nvidia site and installed it.
After loading the driver and restart, the gdm ran, but only for 5 to 10 mins.
The system completely freezes! Can't even ssh in to it from other pc.  Only way to get back is by hard reboot!

So, any suggestions?

---

### Post by tgalati4 on 2009-09-19
I seem to recall a bug where the AGP version of the 6200 card gets the motherboard confused when there is an on-board video chip that also uses AGP.  Try going into the BIOS video settings and turning off the on-board video.

Try using the open drivers.  They don't have the functionality of the proprietary drivers, but they may be more stable.

I have a pci version of the 6200 card that works OK with the proprietary drivers so keep trying different configurations.

---

### Post by Hemal on 2009-09-23
> **tgalati4 said:**
> I seem to recall a bug where the AGP version of the 6200 card gets the motherboard confused when there is an on-board video chip that also uses AGP.  Try going into the BIOS video settings and turning off the on-board video.

Try using the open drivers.  They don't have the functionality of the proprietary drivers, but they may be more stable.

I have a pci version of the 6200 card that works OK with the proprietary drivers so keep trying different configurations.

Great.. Thanks for the suggestion, I will give that a go tonight...

---

### Post by Hemal on 2009-09-26
I could not find any such bios setting.

What am I looking for in the syslog when the crash occurs?

---

### Post by Hemal on 2009-10-02
Upgraded to Karmic Beta, and still no difference.
I wend to Restricted Hardware drivers and then installed Nvidia 185 drivers.  Rebooted the system and then the system just crashed while it was loading gdm.  There was no mouse movement...

---

