---
title: "Cannot connect to internet"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by petruswi on 2009-05-20
Hello,  I installed puppy along with xubuntu for a dual boot.  I couldn't connect to the internet using puppy, so I decided to delete it.  Got back on xubuntu and wasn't able to connect to the internet neither. Reinstalled xubuntu and still not connecting.  It was working on the first install including wireless.  I'm a noob, please let me know what to post.  Thanks!

---

### Post by renzokuken on 2009-05-20
it may be that you have to install/change drivers for your particular wireless card. could you open a terminal and run ```
lspci -v
``` and ```
lsusb -v
``` and post the output of each here so we can identify your particular wireless card (unless you already know what your wireless card is >_<

---

### Post by petruswi on 2009-05-20
> **renzokuken said:**
> it may be that you have to install/change drivers for your particular wireless card. could you open a terminal and run ```
lspci -v
``` and ```
lsusb -v
``` and post the output of each here so we can identify your particular wireless card (unless you already know what your wireless card is >_<

It's an old thinkpad a30.  It's configured to work with the hostap.pci driver and it did work before. Now I can't even get internet through the ethernet.  Thanks for your help.  :)

lspci -v

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
	Subsystem: IBM Device 021d
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: e0000000-e7ffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
	Subsystem: IBM Device 0220
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
	Subsystem: IBM Device 0220
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
	Subsystem: IBM Device 0220
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
	I/O behind bridge: 00004000-00008fff
	Memory behind bridge: c0200000-cfffffff
	Prefetchable memory behind bridge: e8000000-f00fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: IBM Device 0220
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
	Subsystem: IBM Device 0220
	Flags: medium devsel, IRQ 11
	I/O ports at 1880 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
	Subsystem: IBM Device 0222
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
	Subsystem: IBM Device 0227
	Flags: medium devsel, IRQ 11
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
	Subsystem: IBM Device 0235
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
	Subsystem: IBM Device 0185
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: e8000000-ebfff000 (prefetchable)
	Memory window 1: c4000000-c7fff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
	Subsystem: IBM Device 0185
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
	Memory window 0: ec000000-effff000 (prefetchable)
	Memory window 1: c8000000-cbfff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
	Subsystem: Actiontec Electronics Inc Device 0406
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f0000000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: hostap_pci
	Kernel modules: hostap_pci, orinoco_pci

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
	Subsystem: IBM Device 0209
	Flags: bus master, medium devsel, latency 66, IRQ 11
	Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 8000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100, eepro100


lsusb -v

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 002: ID 13fe:3123 Kingston Technology Company Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13fe Kingston Technology Company Inc.
  idProduct          0x3123 
  bcdDevice            1.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by renzokuken on 2009-05-20
Well you wireless device is a Prism 2.5 which should in theory work with Ubuntu. it may be that you need to blacklist a couple of conflicting drivers.....as described here

[https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan](https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan)

---

### Post by petruswi on 2009-05-20
> **renzokuken said:**
> Well you wireless device is a Prism 2.5 which should in theory work with Ubuntu. it may be that you need to blacklist a couple of conflicting drivers.....as described here

[https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan](https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan)

still no connection and my wired network is no longer there.  

Here's my ifconfig, lspci and /et/network/interfaces

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:d0:59:b6:32:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:980 (980.0 B)  TX bytes:980 (980.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-20-E0-8B-54-94-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1726 (1.7 KB)
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr 00:20:e0:8b:54:94  
          inet6 addr: fe80::220:e0ff:fe8b:5494/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2016 (2.0 KB)
          Interrupt:11 

/etc/network/interfaces

auto lo
iface lo inet loopback

lspci

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)

---

### Post by petruswi on 2009-05-20
Everything worked before I installed puppy linux as a dual boot.  I was connecting through the ethernet and wireless.  After not connecting with puppy, I decided to delete it and that's when all of my problems started.  Complete reinstall of xubuntu didn't help.

---

### Post by petruswi on 2009-05-20
Anything else I could post? Please help!

---

### Post by petruswi on 2009-05-20
> **renzokuken said:**
> Well you wireless device is a Prism 2.5 which should in theory work with Ubuntu. it may be that you need to blacklist a couple of conflicting drivers.....as described here

[https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan](https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan)

My apologies to you, but it's my router that's causing the problem!!

I appreciate your time and help  :D

---

