---
title: "Lenovo S10-2 &amp; Intel WiMAX/WiFi Link 5050 Series"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by sorokinlinux on 2009-07-10
Hello.

In advance, forgive for my English.

One week ago has got netbook Lenovo S10-2.
After installation Ubuntu 9.04 I can not start WiFi and WiMax interfaces.


Having downloaded and having compiled modules from a site [http://linuxwimax.org/](http://linuxwimax.org/) there was an interface wmx0 (WiMax). But at attempt to activate it does not see a network.

For acquaintance I result the system information

uname -mr
```
2.6.28-13-generic i686
```


lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 5050 Series
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

lspci -v
```

02:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 5050 Series
	Subsystem: Intel Corporation Device 1216
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 56100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

```

lsusb
```
Bus 005 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 005: ID 8086:1406 Intel Corp. 
Bus 001 Device 004: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:0241 Acer, Inc 
```

lsusb -v
```
Bus 001 Device 005: ID 8086:1406 Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x8086 Intel Corp.
  idProduct          0x1406 
  bcdDevice            0.00
  iManufacturer           1 Intel(R) Corporation
  iProduct                2 Intel(R) WiMAX Link 5150
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
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
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
```

iwconfig was return "no wireless extensions."

ifconfig see only wmx0 and eth0 interface
```
wmx0      Link encap:Ethernet  HWaddr 00:1d:e1:07:ed:b1  
          &#1042;&#1042;&#1045;&#1056;&#1061; NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:5 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lsmod | grep i2400
```
i2400m_usb             37376  0 
i2400m                 78340  1 i2400m_usb
wimax                  34436  2 i2400m_usb,i2400m
```

dmesg |grep i2400
```

[ 3402.812237] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3403.064236] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3403.316235] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3403.568229] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3403.820223] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3404.072235] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3404.324235] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3404.576232] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3404.828232] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
[ 3405.080227] i2400m_usb 1-6:1.0: TX: cannot send URB; retrying. tx_msg @32 64 B [0 sent]: -110
.......

```

dmesg |grep Wi
```
[   18.253497] i2400m_usb 1-6:1.0: WiMAX interface wmx0 (00:1d:e1:07:ed:b1) ready
```

lshw -C network
```
  *-network UNCLAIMED
       description: Network controller
       product: WiMAX/WiFi Link 5050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:cb:17:d9
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: wmx0
       serial: 00:1d:e1:07:ed:b1
       capabilities: ethernet physical
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:bc:d0:45:f3:f9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

[SIZE="2"]Please help to understand[/SIZE]

---

