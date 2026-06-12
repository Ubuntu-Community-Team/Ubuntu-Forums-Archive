---
title: "bluetooth dont seem to work."
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by lilrus on 2012-08-17
Hi everyone,
i am new to ubuntu so i am going to give as much information as possible to fix my problem. 
i am using a Dell Inspiron n4010 just install ubuntu with a bit of manual driver installing here and there. the problem is i can't seem to get my bluetooth to work.  My wireless works fine.  I try turning it on and off using the F2 button on the laptop and on right clicking it.  it keep on saying that there's no bluetooth adapter.

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam
Bus 002 Device 003: ID 0bc2:3300 Seagate RSS LLC 
Bus 002 Device 005: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 011: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 012: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 013: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M96 [Mobility Radeon HD 4650]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

i hope that help.

---

### Post by sanderj on 2012-08-17
I'm not a BT user / expert, but

```
Bus 001 Device 011: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
```

looks good.

What's the output of 

```
lsmod | grep -i -e bt -e bluetooth
```

... hopefully some modules, like this on my (Debian) system:

```
pi@raspberrypi ~ $ lsmod | grep -i -e bt -e bluetooth
btusb                  11685  2 
bluetooth             168468  23 btusb,rfcomm,bnep
pi@raspberrypi ~ $
```

HTH

---

### Post by lilrus on 2012-08-17
for 
lsmod | grep -i -e bt -e bluetooth
bluetooth             180104  10 bnep,rfcomm


that's what i got.

---

