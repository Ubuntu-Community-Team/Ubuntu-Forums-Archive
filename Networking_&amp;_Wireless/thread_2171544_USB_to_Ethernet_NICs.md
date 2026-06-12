---
title: "USB to Ethernet NICs"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by peanut99 on 2013-08-31
Hi All.  I'm studying for my CCIE and decided to use Ubuntu over Windows for various reasons.  I purchased multiple USB-to-ethernet NICs (JP1082 NO: 030818) and when I plug them in together, I have some weird issues.  All of the USB to Ethernet NICs seem to receive the same mac-address.  When I plug them into a Windows box, they all receive different mac addresses.  Also, only the first USB-to-Ethernet adapter will receive a standard "eth#" name and the rest are named "rename#".  Anytime I reboot, the "rename#" will change.  Is there a way to permanently change the name of each USB to Ethernet NIC to a standard "eth#"?  Also, is there a reason that all of my NICs get the same mac address?  I've attached a screen shot of my issue.  Notice eth3's mac address is the same as the "rename#" mac address.  I'm using Ubuntu 12.04.  Any assistance is greatly appreciated.  Thanks!



[ATTACH=CONFIG]245863[/ATTACH]

---

### Post by zero2xiii on 2013-08-31
Hay,

After you plugged them in, please supply the output of the following for more information on what ubuntu is doing:

```
lsusb -v
lsusb -t
lsmod
dmesg | tail -n 100
```

This should show us how ubuntu is addressing the devices and where the issue might sneak in.

Cheers

---

### Post by peanut99 on 2013-08-31
Thanks for the assistance.  Here's the output from the commands you asked:
```
peanut@ubeezy:~$ lsusb -v


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
  bcdDevice            3.02
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
  bcdDevice            3.02
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
  bcdDevice            3.02
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
  bcdDevice            3.02
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
  bcdDevice            3.02
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
  bcdDevice            3.02
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


Bus 001 Device 029: ID 0fe6:9700 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0fe6 Kontron (Industrial Computer Source / ICS Advent)
  idProduct          0x9700 DM9601 Fast Ethernet Adapter
  bcdDevice            1.01
  iManufacturer           0 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              120mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1


Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc52b Unifying Receiver
  bcdDevice           12.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           84
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
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
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
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
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     148
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      98
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               2


Bus 001 Device 030: ID 0fe6:9700 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0fe6 Kontron (Industrial Computer Source / ICS Advent)
  idProduct          0x9700 DM9601 Fast Ethernet Adapter
  bcdDevice            1.01
  iManufacturer           0 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              120mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
peanut@ubeezy:~$ lsusb -t
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
        |__ Port 6: Dev 3, If 0, Class=HID, Driver=usbhid, 12M
        |__ Port 6: Dev 3, If 1, Class=HID, Driver=usbhid, 12M
        |__ Port 6: Dev 3, If 2, Class=HID, Driver=usbhid, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 5: Dev 29, If 0, Class=>ifc, Driver=dm9601, 12M
        |__ Port 6: Dev 30, If 0, Class=>ifc, Driver=dm9601, 12M
peanut@ubeezy:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  4 
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               287130  3 vboxpci,vboxnetadp,vboxnetflt
nvidia              11308613  42 
snd_hda_codec_realtek   224173  1 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
mxm_wmi                13021  0 
sparse_keymap          13890  1 asus_wmi
dm9601                 13579  0 
usbnet                 26212  1 dm9601
joydev                 17693  0 
psmouse                97519  0 
serio_raw              13211  0 
sb_edac                18127  0 
edac_core              53746  1 sb_edac
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              17764  1 snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
mei                    41616  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
bnep                   18281  2 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
wmi                    19256  2 asus_wmi,mxm_wmi
rfcomm                 47604  0 
bluetooth             180113  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech_dj        18730  0 
firewire_ohci          41000  0 
usbhid                 47238  1 hid_logitech_dj
r8169                  62190  0 
firewire_core          63600  1 firewire_ohci
hid                    99636  2 hid_logitech_dj,usbhid
crc_itu_t              12707  1 firewire_core
e1000e                156873  0 
peanut@ubeezy:~$ dmesg | tail -n 100
[58351.095042] usb 1-1.5.2: new full-speed USB device number 14 using ehci_hcd
[58351.111189] udevd[3559]: renamed network interface eth2 to eth3
[58351.169005] dm9601 1-1.5.1:1.0: eth3: link up, 100Mbps, full-duplex, lpa 0xFFFF
[58351.218722] dm9601 1-1.5.2:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.2, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58351.287551] udevd[3559]: renamed network interface eth2 to rename13
[58351.290953] usb 1-1.5.3: new full-speed USB device number 15 using ehci_hcd
[58351.400624] dm9601 1-1.5.3:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.3, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58351.470974] usb 1-1.5.4: new full-speed USB device number 16 using ehci_hcd
[58351.479247] udevd[3659]: renamed network interface eth2 to rename14
[58351.581168] dm9601 1-1.5.4:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.4, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58351.655281] udevd[7568]: renamed network interface eth2 to rename15
[58357.667602] usb 1-1.5: USB disconnect, device number 12
[58357.667608] usb 1-1.5.1: USB disconnect, device number 13
[58357.667727] dm9601 1-1.5.1:1.0: eth3: unregister 'dm9601' usb-0000:00:1a.0-1.5.1, Davicom DM9601 USB Ethernet
[58357.671610] usb 1-1.5: clear tt 1 (10d2) error -71
[58357.671617] usb 1-1.5: clear tt 1 (90d1) error -19
[58357.718170] usb 1-1.5.2: USB disconnect, device number 14
[58357.718249] dm9601 1-1.5.2:1.0: rename13: unregister 'dm9601' usb-0000:00:1a.0-1.5.2, Davicom DM9601 USB Ethernet
[58357.774454] udevd[7568]: renamed network interface rename15 to eth3
[58357.826002] usb 1-1.5.3: USB disconnect, device number 15
[58357.826066] dm9601 1-1.5.3:1.0: rename14: unregister 'dm9601' usb-0000:00:1a.0-1.5.3, Davicom DM9601 USB Ethernet
[58357.866071] usb 1-1.5.4: USB disconnect, device number 16
[58357.866139] dm9601 1-1.5.4:1.0: eth3: unregister 'dm9601' usb-0000:00:1a.0-1.5.4, Davicom DM9601 USB Ethernet
[58464.740147] usb 1-1.5: new high-speed USB device number 17 using ehci_hcd
[58464.833046] hub 1-1.5:1.0: USB hub found
[58464.833224] hub 1-1.5:1.0: 4 ports detected
[58465.104112] usb 1-1.5.1: new high-speed USB device number 18 using ehci_hcd
[58465.196999] hub 1-1.5.1:1.0: USB hub found
[58465.197177] hub 1-1.5.1:1.0: 4 ports detected
[58465.268044] usb 1-1.5.2: new high-speed USB device number 19 using ehci_hcd
[58465.360979] hub 1-1.5.2:1.0: USB hub found
[58465.361128] hub 1-1.5.2:1.0: 4 ports detected
[58465.432042] usb 1-1.5.3: new high-speed USB device number 20 using ehci_hcd
[58465.524959] hub 1-1.5.3:1.0: USB hub found
[58465.525101] hub 1-1.5.3:1.0: 4 ports detected
[58465.612027] usb 1-1.5.4: new full-speed USB device number 21 using ehci_hcd
[58465.737208] dm9601 1-1.5.4:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.4, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58465.824001] usb 1-1.5.1.2: new full-speed USB device number 22 using ehci_hcd
[58465.836326] udevd[7615]: renamed network interface eth2 to eth3
[58465.895120] dm9601 1-1.5.4:1.0: eth3: link up, 100Mbps, full-duplex, lpa 0xFFFF
[58465.993570] dm9601 1-1.5.1.2:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.1.2, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58466.052361] udevd[7615]: renamed network interface eth2 to rename17
[58466.079910] usb 1-1.5.1.3: new full-speed USB device number 23 using ehci_hcd
[58466.204022] dm9601 1-1.5.1.3:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.1.3, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58466.252411] udevd[7616]: renamed network interface eth2 to rename18
[58466.291944] usb 1-1.5.2.2: new full-speed USB device number 24 using ehci_hcd
[58466.418143] dm9601 1-1.5.2.2:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.2.2, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58466.503887] usb 1-1.5.2.3: new full-speed USB device number 25 using ehci_hcd
[58466.512398] udevd[7744]: renamed network interface eth2 to rename19
[58466.627950] dm9601 1-1.5.2.3:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.2.3, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58466.696428] udevd[7789]: renamed network interface eth2 to rename20
[58466.715853] usb 1-1.5.3.1: new full-speed USB device number 26 using ehci_hcd
[58466.840156] dm9601 1-1.5.3.1:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.3.1, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58466.912416] udevd[7803]: renamed network interface eth2 to rename21
[58466.927831] usb 1-1.5.3.2: new full-speed USB device number 27 using ehci_hcd
[58467.056390] dm9601 1-1.5.3.2:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.3.2, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58467.143838] usb 1-1.5.3.4: new full-speed USB device number 28 using ehci_hcd
[58467.152412] udevd[7817]: renamed network interface eth2 to rename22
[58467.276798] dm9601 1-1.5.3.4:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5.3.4, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58467.372505] udevd[7831]: renamed network interface eth2 to rename23
[58476.930365] eth3: no IPv6 routers present
[58507.752540] usb 1-1.5: clear tt 1 (1152) error -71
[58507.756652] usb 1-1.5: clear tt 1 (9151) error -71
[58507.760776] usb 1-1.5: clear tt 1 (1152) error -71
[58507.764899] usb 1-1.5: clear tt 1 (9151) error -71
[58507.769097] usb 1-1.5: clear tt 1 (1152) error -71
[58507.773184] usb 1-1.5: clear tt 1 (9151) error -71
[58507.781150] usb 1-1.5: clear tt 1 (9151) error -71
[58507.788532] usb 1-1.5: USB disconnect, device number 17
[58507.788538] usb 1-1.5.1: USB disconnect, device number 18
[58507.788542] usb 1-1.5.1.2: USB disconnect, device number 22
[58507.788625] dm9601 1-1.5.1.2:1.0: rename17: unregister 'dm9601' usb-0000:00:1a.0-1.5.1.2, Davicom DM9601 USB Ethernet
[58507.838669] usb 1-1.5.1.3: USB disconnect, device number 23
[58507.838739] dm9601 1-1.5.1.3:1.0: rename18: unregister 'dm9601' usb-0000:00:1a.0-1.5.1.3, Davicom DM9601 USB Ethernet
[58507.879029] usb 1-1.5.2: USB disconnect, device number 19
[58507.879036] usb 1-1.5.2.2: USB disconnect, device number 24
[58507.879115] dm9601 1-1.5.2.2:1.0: rename19: unregister 'dm9601' usb-0000:00:1a.0-1.5.2.2, Davicom DM9601 USB Ethernet
[58507.918618] usb 1-1.5.2.3: USB disconnect, device number 25
[58507.918685] dm9601 1-1.5.2.3:1.0: rename20: unregister 'dm9601' usb-0000:00:1a.0-1.5.2.3, Davicom DM9601 USB Ethernet
[58507.962975] usb 1-1.5.3: USB disconnect, device number 20
[58507.962983] usb 1-1.5.3.1: USB disconnect, device number 26
[58507.963073] dm9601 1-1.5.3.1:1.0: rename21: unregister 'dm9601' usb-0000:00:1a.0-1.5.3.1, Davicom DM9601 USB Ethernet
[58508.014676] usb 1-1.5.3.2: USB disconnect, device number 27
[58508.014759] dm9601 1-1.5.3.2:1.0: rename22: unregister 'dm9601' usb-0000:00:1a.0-1.5.3.2, Davicom DM9601 USB Ethernet
[58508.054693] usb 1-1.5.3.4: USB disconnect, device number 28
[58508.054795] dm9601 1-1.5.3.4:1.0: rename23: unregister 'dm9601' usb-0000:00:1a.0-1.5.3.4, Davicom DM9601 USB Ethernet
[58508.095070] usb 1-1.5.4: USB disconnect, device number 21
[58508.095162] dm9601 1-1.5.4:1.0: eth3: unregister 'dm9601' usb-0000:00:1a.0-1.5.4, Davicom DM9601 USB Ethernet
[58514.829700] usb 1-1.5: new full-speed USB device number 29 using ehci_hcd
[58514.938947] dm9601 1-1.5:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.5, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58515.021977] udevd[7920]: renamed network interface eth2 to eth3
[58515.080526] dm9601 1-1.5:1.0: eth3: link up, 100Mbps, full-duplex, lpa 0xFFFF
[58515.165616] usb 1-1.6: new full-speed USB device number 30 using ehci_hcd
[58515.279092] dm9601 1-1.6:1.0: eth2: register 'dm9601' at usb-0000:00:1a.0-1.6, Davicom DM9601 USB Ethernet, 00:e0:4c:53:44:58
[58515.338003] udevd[7920]: renamed network interface eth2 to rename25
[58525.528050] eth3: no IPv6 routers present
[58560.615593] ADDRCONF(NETDEV_UP): eth3: link is not ready
[58563.407363] ADDRCONF(NETDEV_UP): eth3: link is not ready
[58563.407566] ADDRCONF(NETDEV_UP): eth3: link is not ready
[58608.602490] ADDRCONF(NETDEV_UP): eth3: link is not ready
peanut@ubeezy:~$ 

```

Let me know if you need any additional output.  Thanks!

-Peanut

---

### Post by zero2xiii on 2013-08-31
Hay,

Yea just as I expected, it is a driver issue. I'll look around on how to fix that just now.

First, try and shift one of the two (from the output I only see 2 additional controlers?) controlers to another USB port (Move it to a USB 3 port just to be sure it gets moved off of the same root hub).

See if this fixes the issue, also why do you need 3 ethernet interfaces?

If the above does not solve the issue you can start by:

```
#Make a backup of the file:
cp /etc/udev/rules.d/70-persistent-net.rules ~/70-persistent-net.rules.bak
#Open file as sudo for editing
sudo nano /etc/udev/rules.d/70-persistent-net.rules
```

Now in there you can rename the devices as you wish. Also please post the output of:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

I have no idea why your 2 devices has the same MAC address. I think this is because the driver is loaded only once:
> dm9601                 13579  0 
usbnet                 26212  **1** dm9601

It is hard for me to explain in detail what to edit since I can by no means duplicate your set up. But I will try my best if you supply the file above and have already tried changing the names appropriately.

Cheers and good luck

---

### Post by peanut99 on 2013-08-31
Thanks again for the assistance.  I actually need 12 of these USB to ethernet adapters to bridge my physical hardware (Cisco Switches) into GNS3.  I'll mess around with the file you mentioned.  Here's the output:

```
peanut@ubeezy:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.7/0000:0a:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="64:66:b3:02:27:40", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c8:60:00:0a:17:73", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# USB device 0x0b95:0x772b (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:00:00:0f:2b:f2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# USB device 0x0fe6:0x9700 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:4c:53:44:58", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"
peanut@ubeezy:~$ 
```

---

### Post by zero2xiii on 2013-08-31
Hay,

I see all different mac's in that post. Maybe you can try this to change the macs if it gives issues (as in the original post's screenshot)

[http://www.ubuntugeek.com/macchanger-utility-for-manipulating-the-mac-address-of-network-interfaces-included-gui-utility.html](http://www.ubuntugeek.com/macchanger-utility-for-manipulating-the-mac-address-of-network-interfaces-included-gui-utility.html)

Hmm interesting concept on bridging them all (12 over USB? wow)

I wish I could duplicate the setup to give more clean cut answers.

---

### Post by houstonbofh on 2013-08-31
USB makes all of this much more complex than it needs to be, especially with 12 of them.  The thing is Ubuntu can never know which one will "answer first" and so the order is based on mac address...  If that fails, everything behind it fails.  I would consider trying with some Intel dual port pci-e nics.  They go for $20 on eBay.

---

