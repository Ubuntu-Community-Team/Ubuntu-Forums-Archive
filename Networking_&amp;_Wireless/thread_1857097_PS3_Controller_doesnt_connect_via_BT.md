---
title: "PS3 Controller doesnt connect via BT"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by ceejay85 on 2011-10-09
Hi there,

The entire day I am trying to connect my org PS3 Controller to my Ubuntu PC.
I tried different tutorials and settings [like this ]("http://www.wiredrevolution.com/ubuntu/setup-the-ps3-bluetooth-controller-on-ubuntu") or [this]("http://qtsixa.sourceforge.net/") but nothing seems to work. There is no Error MSG. It is just not connecting.
I tested with Mini Ubuntu 10.10 and 11.04. The only thing I have also installed is xbmc, so I have no GUI.
When I connect the Controller via USB it works fine. 

Hardware is a ASROCK ION330 with [this USB BT Dongle]("http://www.ebay.de/itm/330577918752?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649#ht_4166wt_1396")

The only result that I get is a none stop blinking controller :(

```

xbmc@xbmc:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
xbmc@xbmc:~$ lsusb
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any additional Info needed?

---

