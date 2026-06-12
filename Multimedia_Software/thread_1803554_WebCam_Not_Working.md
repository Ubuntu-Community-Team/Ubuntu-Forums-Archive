---
title: "WebCam Not Working"
date: 2011-07-13
forum: Multimedia Software
---

### Post by calebi on 2011-07-13
So I had my webcam working on Ubuntu 10.10 but it crashed so I installed 11.04 and now it doesn't work. When I run lsusb, this is what I get:
```

caleb@caleb-A6200:~$ lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```And this is lspci
```

caleb@caleb-A6200:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```I tried using Cheese and I get an error saying that "/dev/video0" does not exist. Any thoughts?

Thanks,
Caleb

---

### Post by no2498 on 2011-07-13
look in your package manager for xawtv install it
after installed in a terminal type dmesg click enter
now try the cam in xawtv

---

### Post by calebi on 2011-07-13
```

caleb@caleb-A6200:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.38-10-generic-pae)
xinerama 0: 1366x768+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device or address
v4l2: open /dev/video0: No such device or address
v4l: open /dev/video0: No such device or address
no video grabber device available

```

---

### Post by no2498 on 2011-07-14
change it to say xawtv not skype
put it in a terminal    click enter



AmyRose
November 24th, 2008, 08:15 PM
In Intrepid, to fix this problem, I installed the libv4l-0 package and preload it with Skype like this:

 env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

