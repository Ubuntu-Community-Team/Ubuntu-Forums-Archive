---
title: "Wireless Troubleshooting Guide dead end"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by irvken on 2011-09-14
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("http://https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

I don’t know how “official” this is (can anything be that official in Open Source other than the licence) but I have entered a dead end dilemma in following it.

If I lay out the steps maybe someone can see where I went wrong, suggest something else or at least suggest better documentation

> 2. Quick Check

   1. With your computer turned off, insert your wireless adapter into a suitable port/slot.
   2. Turn on your computer and log-in if/when prompted.
   3. Open a terminal window and enter the following command: [FONT="Courier New"]nm-tool[/FONT]


```
neave@KING:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
 Type:              Wired
 Driver:            forcedeth
 State:             connected
 Default:           yes
 HW Address:        F4:6D:04:93:47:B3

 Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

 Wired Properties
    Carrier:         on

 IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             194.168.4.100
    DNS:             194.168.8.100


neave@KING:~$
```


So the machine does not seem to have detected the wifi dongle. If this is the case 3.1 tells you to refer to

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices]("http://https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices")

> 1. Open a terminal window and type:
lshw -C network

```
neave@KING:~$ sudo lshw -C network
neave@KING:~$
```

As you can see no output.

If that is the case the documentation says I should work through this section

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lsusb]("http://https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lsusb")

This is just a page explaining how relevant bash command work

> sudo lsusb -v

The relevant output is

```
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp.
Device Descriptor:
 bLength                18
 bDescriptorType         1
 bcdUSB               2.00
 bDeviceClass            0 (Defined at Interface level)
 bDeviceSubClass         0
 bDeviceProtocol         0
 bMaxPacketSize0        64
 idVendor           0x148f Ralink Technology, Corp.
 idProduct          0x2070
 bcdDevice            1.01
 iManufacturer           1 Ralink
 iProduct                2 802.11 g WLAN
 iSerial                 3 1.0
 bNumConfigurations      1
 Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
     (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       0
     bNumEndpoints           7
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass    255 Vendor Specific Subclass
     bInterfaceProtocol    255 Vendor Specific Protocol
     iInterface              5 1.0
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x81  EP 1 IN
       bmAttributes            2
         Transfer Type            Bulk
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0200  1x 512 bytes
       bInterval               0
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
       bEndpointAddress     0x02  EP 2 OUT
       bmAttributes            2
         Transfer Type            Bulk
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0200  1x 512 bytes
       bInterval               0
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
       bEndpointAddress     0x04  EP 4 OUT
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
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x06  EP 6 OUT
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
Device Status:     0x0000
 (Bus Powered)
```

So the machine CAN see the device, but then it doesn’t say what to donext!! Whenever I start again I just seem to end up here. So again, maybe someone can see where I went wrong, suggest something else or at least suggest better documentation.

Cheers

---

