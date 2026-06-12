---
title: "So Close! Ralink driver almost working..."
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by Hilarius on 2006-01-17
I have a Wireless card that I know works in Ubuntu.. a Belkin FD7050 Wireless G.

I have been following the instructions at Lambert's tutorial for the rt2570 drivers and many other different places: all which seem to rely on "iwconfig rausb0" commands.

All the modules are installed, and everything seemed bright.

Unfortunately, rausb0 NEVER comes up for me, anywhere, ever. I mean, rausb0 never even appears as a networking option. My computer contains no references to rausb0 except the ones I explicity have edited it (/etc/modules.conf)

I've rebooted, installed scores of drivers from ralink (still have rt2570 on...), and I feel it should work. Is there something special I need to interface with rausb0 device? Do I need to run some scripts? 

Lshw returns this:

*-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: Belkin 54g USB Network Adapter
                   vendor: Belkin
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: maxpower=300mA speed=12.0MB/s

---

### Post by gosh on 2006-01-17
do you have any other usb devices working?
I read here that [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B) that might cause trouble
[SIZE="1"]
# Card: Belkin F5D7050 (USB 2.0 Adaptor 802.11g 54Mbps)

    * Chipset: Conexant (PrismUSB)
    * usbid: 050D:7050
    * Driver: Install the drivers for windows included in the box and fetch the .inf and .sys fyles from the installation directory.
    * Other: linux-2.6.9: Blocks Linux momentarily when another device is plugged into the same USB Hub, more precisely a 1.1 memory stick.
    * Other: SuSE 9.1, kernel-2.6.8-default (kernel-of-the-day 22 Dec. 2004): 1.0rc1 with bknUSB.inf from the vendor CD and WEP security works quite stable. The procedure as described in WiKi/SuSE 9.1. Professional.
    * Other: SuSE 9.1, kernel-2.6.x-smp: doesn't work, 'modprobe ndiswrapper' freezes the system. 

[/SIZE]

---

### Post by Lambert on 2006-01-17
There currently is no driver bound to the device from that lshw output.

So make sure it's loaded.

lsmod | grep rt

also post the output of *lsusb -v*

---

### Post by Hilarius on 2006-01-17
I have a usb mouse and keyboard, so i assume the ports are active. I have also used a memory stick before in the port I have the card plugged in.


Here is lsmod | grep rt
```
 gameport               14472  1 snd_ens1371
agpgart                32328  1 intel_agp
rt2570                155328  0
parport_pc             31812  1
parport                32072  2 parport_pc,lp
usbcore               104188  4 rt2570,usbhid,uhci_hcd

```


Here is lsusb -v
```
Bus 002 Device 003: ID 050d:705a Belkin Components
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705a
  bcdDevice            0.01
  iManufacturer           1 Belkin
  iProduct                2 Belkin 54g USB Network Adapter
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1[CODE]
```
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
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

Bus 002 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc00e Optical Mouse
  bcdDevice           11.10
  iManufacturer           1 Logitech
  iProduct                2 USB-PS/2 Optical Mouse
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-9-386 uhci_hcd
  iProduct                2 Intel Corporation 82801BA/BAM USB (Hub #2)
  iSerial                 1 0000:00:1f.4
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x50
  PortPwrCtrlMask    0x81
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0103 power enable connect

Bus 001 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x1267 Logic3 / SpectraVideo plc
  idProduct          0x0103
  bcdDevice            1.01
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-9-386 uhci_hcd
  iProduct                2 Intel Corporation 82801BA/BAM USB (Hub #1)
  iSerial                 1 0000:00:1f.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0x12
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
[/CODE]

---

### Post by The_Jack on 2006-04-12
Bump

I get the same as you when I type in lsmod | grep rt and also when I type lsusb -v. 

Did you ever solve what to do or anyone else know what the fix may be?

---

### Post by jono.carnie on 2006-05-26
Bump.....
Exactly the same problem here...
Followed all the guides I've managed to find so far and I just can't seem to manage to get the driver loaded?

Running Dapper with 2.6.15-21-386.

JC

---

### Post by jono.carnie on 2006-05-28
Anyone with this problem take a look at [http://ubuntuforums.org/showthread.php?p=1061193#post1061193]("http://ubuntuforums.org/showthread.php?p=1061193#post1061193")

---

### Post by Fisslefink on 2006-06-06
I hate to taunt you with a success story, but I have been running Dapper pre-release since April, and Hoary and Breezy before that, with my Belkin F5D7050 USB key.

In Breezy and Hoary, I had to compile drivers myself from the tarball located on this site:  [http://rt2400.cvs.sourceforge.net/rt2400/source/rt2570/](http://rt2400.cvs.sourceforge.net/rt2400/source/rt2570/)

When I installed Dapper (fresh install from discs), it loaded the rt2570 module by itself (see below)
```

fisslefink@dapperbox:/boot/grub$ lsmod|grep rt2570
rt2570                200160  1
usbcore               137700  6 islsm_usb,rt2570,usbhid,ehci_hcd,uhci_hcd
```

This built in driver works fine except for kernel freezes if I unplug it without warning or if I try to get an IP by DHCP too many times in a row.  See related bug report here: [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=162&sid=e6caff15cbaa2c62bac6a39f3a9ef7e7](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=162&sid=e6caff15cbaa2c62bac6a39f3a9ef7e7)

Now, however, there are more options for drivers.  The rt2570usb driver has evolved into the rt2x00 driver, and a new driver called "Ural" has appeared. The differences are summarized nicely here: [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=674&](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=674&)

Sorry I don't have time to walk you through getting your driver working, but it can be done.  I hope this info will get you pointed in the right direction.  The people on the [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) forums are very helpful, I would go there with future questions.

Fisslefink

---

### Post by escapee from Winhell on 2006-06-06
I wish i'd seen this earlier..I'm having a problem getting my f5d7050 usb adapter to work altogether....i us the ndiswrapper and the windows drivers..inf and .sys files...says driver present hardware present but won't connect...however through forums i've found sites that have instructed me that being my version (v.3000) uses the rt73 driver from ralink that i needed to use it...that's where i'm lost...the driver has to be built but i can't get past the makefile command of building it for some reason...if anyone manages to get the Belkin F5D7050 (using the rt73 driver..if that matters..not sure ) to work... please let me know how it was accomplished..i'm also gonna try to set up a linksys wusb54g adapter..whichever i get working i will post in forums...thanks for any and all help

---

