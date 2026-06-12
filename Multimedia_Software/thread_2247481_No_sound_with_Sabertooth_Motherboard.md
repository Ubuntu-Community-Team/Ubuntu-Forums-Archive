---
title: "No sound with Sabertooth Motherboard"
date: 2014-10-08
forum: Multimedia Software
---

### Post by mark1977 on 2014-10-08
Hi,
I cannot get sound from any application. I have Ubuntu 12.04 with an Asus Sabertooth X79 motherboard.
I don't want to upgrade to 14 for a while because I am afraid of breaking things.
I tried following the advice here: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
but it didn't help.
Alsamixer looks fine (nothing muted).
Hopefully this is some useful info:
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```


```
$ lsusb -v

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0024 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0024 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
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
        bInterval              12

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.05
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.05
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.05
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.05
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.05
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.05
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.05
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.05
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0

Bus 002 Device 061: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x0024 KU-0316 Keyboard
  bcdDevice            3.00
  iManufacturer           1 
  iProduct                2 
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
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
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
          wDescriptorLength      65
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

Bus 002 Device 062: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0458 KYE Systems Corp. (Mouse Systems)
  idProduct          0x003a NetScroll+ Mini Traveler / Genius NetScroll 120
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
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
          wDescriptorLength      62
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


```



```
$ pactl list
Module #0
    Name: module-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "1.1"

Module #1
    Name: module-stream-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "1.1"

Module #2
    Name: module-card-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore profile of cards"
        module.version = "1.1"

Module #3
    Name: module-augment-properties
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Augment the property sets of streams with additional static information"
        module.version = "1.1"

Module #4
    Name: module-alsa-card
    Argument: device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "1.1"

Module #5
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 1
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "1.1"

Module #6
    Name: module-udev-detect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "1.1"

Module #7
    Name: module-bluetooth-discover
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Joao Paulo Rechi Vita"
        module.description = "Detect available bluetooth audio devices and load bluetooth audio drivers"
        module.version = "1.1"

Module #8
    Name: module-native-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "1.1"

Module #9
    Name: module-gconf
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "GConf Adapter"
        module.version = "1.1"

Module #10
    Name: module-default-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "1.1"

Module #11
    Name: module-rescue-streams
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
        module.version = "1.1"

Module #12
    Name: module-always-sink
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "1.1"

Module #13
    Name: module-intended-roles
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically set device of streams based of intended roles of devices"
        module.version = "1.1"

Module #14
    Name: module-suspend-on-idle
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "1.1"

Module #15
    Name: module-console-kit
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each ConsoleKit session of this user"
        module.version = "1.1"

Module #16
    Name: module-position-event-sounds
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "1.1"

Module #17
    Name: module-filter-heuristics
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Detect when various filters are desirable"
        module.version = "1.1"

Module #18
    Name: module-filter-apply
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Load filter sinks automatically when needed"
        module.version = "1.1"

Module #19
    Name: module-switch-on-port-available
    Argument: 
    Usage counter: n/a
    Properties:
        

Module #20
    Name: module-x11-publish
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 credential publisher"
        module.version = "1.1"

Module #21
    Name: module-x11-bell
    Argument: display=:0 sample=bell.ogg
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 bell interceptor"
        module.version = "1.1"

Module #22
    Name: module-x11-cork-request
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Synthesize X11 media key events when cork/uncork is requested"
        module.version = "1.1"

Module #23
    Name: module-x11-xsmp
    Argument: display=:0 session_manager=local/osi:@/tmp/.ICE-unix/2342,unix/osi:/tmp/.ICE-unix/2342
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 session management"
        module.version = "1.1"

Sink #0
    State: SUSPENDED
    Name: alsa_output.pci-0000_01_00.1.hdmi-stereo
    Description: GF114 HDMI Audio Controller Digital Stereo (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 4
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor Source: alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xfa080000 irq 36"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.name = "GF114 HDMI Audio Controller"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "GF114 HDMI Audio Controller Digital Stereo (HDMI)"
        alsa.mixer_name = "Nvidia GPU 16 HDMI/DP"
        alsa.components = "HDA:10de0016,10de0101,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, not available)
    Active Port: hdmi-output-0
    Formats:
        pcm

Sink #1
    State: RUNNING
    Name: alsa_output.pci-0000_00_1b.0.analog-stereo
    Description: Built-in Audio Analogue Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 5
    Mute: no
    Volume: 0: 125% 1: 125%
            0: 5.90 dB 1: 5.90 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
    Latency: 80187 usec, configured 90000 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC892 Analog"
        alsa.id = "ALC892 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfa720000 irq 93"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "C600/X79 series chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analogue Stereo"
        device.description = "Built-in Audio Analogue Stereo"
        alsa.mixer_name = "Realtek ALC892"
        alsa.components = "HDA:10ec0892,10438436,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-output: Analogue Output (priority: 9900)
        analog-output-headphones: Headphones (priority: 9000, available)
    Active Port: analog-output-headphones
    Formats:
        pcm

Source #0
    State: SUSPENDED
    Name: alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor
    Description: Monitor of GF114 HDMI Audio Controller Digital Stereo (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 4
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor of Sink: alsa_output.pci-0000_01_00.1.hdmi-stereo
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of GF114 HDMI Audio Controller Digital Stereo (HDMI)"
        device.class = "monitor"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xfa080000 irq 36"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.name = "GF114 HDMI Audio Controller"
        device.string = "1"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Formats:
        pcm

Source #1
    State: IDLE
    Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
    Description: Monitor of Built-in Audio Analogue Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 5
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor of Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
    Latency: 0 usec, configured 371519 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Built-in Audio Analogue Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfa720000 irq 93"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "C600/X79 series chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Formats:
        pcm

Source #2
    State: SUSPENDED
    Name: alsa_input.pci-0000_00_1b.0.analog-stereo
    Description: Built-in Audio Analogue Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 5
    Mute: no
    Volume: 0:  11% 1:  11%
            0: -57.51 dB 1: -57.51 dB
            balance 0.00
    Base Volume:  10%
                 -60.00 dB
    Monitor of Sink: n/a
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC892 Analog"
        alsa.id = "ALC892 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfa720000 irq 93"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "C600/X79 series chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analogue Stereo"
        device.description = "Built-in Audio Analogue Stereo"
        alsa.mixer_name = "Realtek ALC892"
        alsa.components = "HDA:10ec0892,10438436,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-input-microphone-front: Front Microphone (priority: 8500, not available)
        analog-input-microphone-rear: Rear Microphone (priority: 8200, available)
        analog-input-linein: Line In (priority: 8100, not available)
    Active Port: analog-input-microphone-rear
    Formats:
        pcm

Sink Input #42
    Driver: protocol-native.c
    Owner Module: 8
    Client: 28
    Sink: 1
    Sample Specification: float32le 2ch 44100Hz
    Channel Map: front-left,front-right
    Format: pcm, format.sample_format = "\"float32le\""  format.channels = "2"  format.rate = "44100"  format.channel_map = "\"front-left,front-right\""
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Buffer Latency: 101383 usec
    Sink Latency: 79831 usec
    Resample method: copy
    Properties:
        media.name = "'Absolute Radio' by 'Absolute Radio'"
        application.name = "Rhythmbox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        media.role = "music"
        application.process.id = "31993"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "rhythmbox"
        application.icon_name = "rhythmbox"
        application.language = "en_GB.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"
        module-stream-restore.id = "sink-input-by-media-role:music"
        media.title = "Absolute Radio"
        media.artist = "Absolute Radio"

Client #0
    Driver: module-console-kit.c
    Owner Module: 15
    Properties:
        application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
        console-kit.session = "/org/freedesktop/ConsoleKit/Session2"

Client #1
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "GNOME Volume Control Media Keys"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = "3.4.2"
        application.process.id = "2391"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "gnome-settings-daemon"
        application.language = "en_GB.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"

Client #3
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "Indicator Sound"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        application.id = "com.canonical.indicator.sound"
        application.icon_name = "multimedia-volume-control"
        application.version = "0.8.5.0"
        application.process.id = "2551"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "indicator-sound-service"
        application.language = "en_GB.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"

Client #8
    Driver: module-x11-xsmp.c
    Owner Module: 23
    Properties:
        application.name = "XSMP Session on gnome-session as 10108da11d1ae95930141224689753119700000023420041"
        xsmp.vendor = "gnome-session"
        xsmp.client.id = "10108da11d1ae95930141224689753119700000023420041"

Client #10
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "Metacity"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        window.x11.display = ":0"
        window.x11.screen = "0"
        application.process.id = "2409"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "metacity"
        application.language = "en_GB.UTF-8"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"

Client #21
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "Firefox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        application.icon_name = "firefox"
        application.version = "32.0.3"
        application.process.id = "21402"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "firefox"
        window.x11.display = ":0"
        application.language = "en_GB.UTF-8"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"

Client #23
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "AudioStream"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        application.process.id = "21402"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "firefox"
        window.x11.display = ":0"
        application.language = "en_GB.UTF-8"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"
        application.icon_name = "firefox"

Client #28
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "Rhythmbox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        media.role = "music"
        application.process.id = "31993"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "rhythmbox"
        application.icon_name = "rhythmbox"
        application.language = "en_GB.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"

Client #38
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        application.process.id = "1019"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "pactl"
        application.language = "en_GB.UTF-8"
        window.x11.display = ":0.0"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"

Sample #0
    Name: bell-window-system
    Sample Specification: s16le 1ch 44100Hz
    Channel Map: mono
    Volume: (invalid)
            (invalid)
            balance 0.00
    Duration: 0.2s
    Size: 17.2 KiB
    Lazy: no
    Filename: n/a
    Properties:
        media.role = "event"
        application.process.id = "5900"
        application.name = "gnome-terminal"
        event.description = "Bell event"
        event.id = "bell-window-system"
        media.name = "bell-window-system"
        media.filename = "/usr/share//sounds/ubuntu/stereo/bell.ogg"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        window.x11.display = ":0"
        window.x11.screen = "0"
        application.process.user = "mark"
        application.process.host = "osi"
        application.process.binary = "metacity"
        application.language = "en_GB.UTF-8"
        application.process.machine_id = "330b0cb9bcf85bc930f47ecb0000000c"
        application.process.session_id = "330b0cb9bcf85bc930f47ecb0000000c-1412246886.660406-1950672934"

Card #0
    Name: alsa_card.pci-0000_01_00.1
    Driver: module-alsa-card.c
    Owner Module: 4
    Properties:
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xfa080000 irq 36"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.name = "GF114 HDMI Audio Controller"
        device.string = "1"
        device.description = "GF114 HDMI Audio Controller"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5400)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 300)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5200)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 100)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5200)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 100)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5200)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 100)
        off: Off (sinks: 0, sources: 0, priority. 0)
    Active Profile: output:hdmi-stereo
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900)
            Part of profile(s): output:hdmi-stereo, output:hdmi-surround
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800)
            Part of profile(s): output:hdmi-stereo-extra1, output:hdmi-surround-extra1
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700)
            Part of profile(s): output:hdmi-stereo-extra2, output:hdmi-surround-extra2
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600)
            Part of profile(s): output:hdmi-stereo-extra3, output:hdmi-surround-extra3

Card #1
    Name: alsa_card.pci-0000_00_1b.0
    Driver: module-alsa-card.c
    Owner Module: 5
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfa720000 irq 93"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "C600/X79 series chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:analog-stereo: Analogue Stereo Output (sinks: 1, sources: 0, priority. 6000)
        output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
        output:analog-surround-40: Analogue Surround 4.0 Output (sinks: 1, sources: 0, priority. 700)
        output:analog-surround-40+input:analog-stereo: Analogue Surround 4.0 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 760)
        output:analog-surround-41: Analogue Surround 4.1 Output (sinks: 1, sources: 0, priority. 800)
        output:analog-surround-41+input:analog-stereo: Analogue Surround 4.1 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 860)
        output:analog-surround-50: Analogue Surround 5.0 Output (sinks: 1, sources: 0, priority. 700)
        output:analog-surround-50+input:analog-stereo: Analogue Surround 5.0 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 760)
        output:analog-surround-51: Analogue Surround 5.1 Output (sinks: 1, sources: 0, priority. 800)
        output:analog-surround-51+input:analog-stereo: Analogue Surround 5.1 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 860)
        output:analog-surround-71: Analog Surround 7.1 Output (sinks: 1, sources: 0, priority. 700)
        output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 760)
        output:iec958-stereo: Digital Stereo (IEC958) Output (sinks: 1, sources: 0, priority. 5500)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 5560)
        input:analog-stereo: Analogue Stereo Input (sinks: 0, sources: 1, priority. 60)
        off: Off (sinks: 0, sources: 0, priority. 0)
    Active Profile: output:analog-stereo+input:analog-stereo
    Ports:
        analog-output: Analogue Output (priority 9900)
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-40, output:analog-surround-40+input:analog-stereo, output:analog-surround-41, output:analog-surround-41+input:analog-stereo, output:analog-surround-50, output:analog-surround-50+input:analog-stereo, output:analog-surround-51, output:analog-surround-51+input:analog-stereo, output:analog-surround-71, output:analog-surround-71+input:analog-stereo
        analog-output-headphones: Headphones (priority 9000)
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo
        analog-input-microphone-front: Front Microphone (priority 8500)
            Part of profile(s): output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
        analog-input-microphone-rear: Rear Microphone (priority 8200)
            Part of profile(s): output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
        analog-input-linein: Line In (priority 8100)
            Part of profile(s): output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0)
            Part of profile(s): output:iec958-stereo, output:iec958-stereo+input:analog-stereo


```

Appreciate any help, thanks.

---

### Post by oceola2 on 2014-10-09
I'm running both 14.04.1 and 12.04.5 on a Sabertooth Z77, Intel based similar to your own with the i& Ivy Bridge processor.
Instead of the nVidia card I'm just using the on-board sounds with separate speakers.
Probably not the answer you were looking for but it could be something to do with the nVidia card more than the Sabertooth.
Some of the packages below were for support fo particular games.
**Installed packages:** Most recent versions of all for both 12 and 14.
Alsa-base; alsa-utils; gstreamer0.10-alsa; gstreamer0.10-plugins-base; gstreamer0.10-plugins-base-apps; 
gstreamer0.10-plugins-good; gstreamer0.10-pulseaudio; gstreamer0.10-tools; gstreamer0.10-x; gstreamer1.0-alsa
gstreamer1.0-plugins-base; gstreamer1.0-plugins-base-apps; gstreamer1.0-plugins-good; gstreamer1.0-pulseaudio
gstreamer1.0-tools; gstreamer1.0-x; indicator-sound; liballegro4.4; liballegro4.4-plugin-alsa; libasound2; libasound2-data; libasound2-plugins
libcanberra-gtk-module; libcanberra-gtk0; libcanberra-gtk3-0; libcanberra-gtk3-module; libcanberra-pulse; libcanberra0
libfluidsynth1; libfreerdp-plugins-standard; libgstreamer-plugins-base0.10-0; libgstreamer-plugins-base1.0-0; libgstreamer-plugins-good1.0-0; libgstreamer0.10-0
libgstreamer1.0-0; libjack-jackd2-0; libmikmod2; libpulse-mainloop-glib0; libpulse0; libpulsedsp; libsdl1.2debian; libsdl-mixer1.2;  libsdl2-2.0-0; linux-sound-base; 
pulseaudio; pulseaudio-module-bluetooth; pulseaudio-module-x11; pulseaudio-utils; sound-theme-freedesktop; ubuntu-sounds

---

