---
title: "Sync program for non-Ipod mp3 player crowd"
date: 2008-11-11
forum: Multimedia Software
---

### Post by BudaTx on 2008-11-11
I tried GPodder and it doesn't seem what I need.  I'm looking for a sync program for non-Ipod generic mp3 USB players.  One that will have library, playlist and show the USB device.  I'm using Xubuntu so I don't know if I'm missing something by not using Ubuntu, but my laptop's a bit older.  And if there is something from Synaptic I don't have to 'hand configure' that will be even better.  I'm using a Dell DJ-Ditty now, but will get an even more generic one this weekend with more mem. (512mb currently), a 1 or 2gb for $19.  
Thx

---

### Post by nonzer0 on 2008-12-11
Me too!  Ive been looking for a file manager for my Dell DJ Gen2 Player for about 2 months now.  Can't find one.  Gnomad2 latest version doesn't work, even as root, Neutrino does nothing, Amorok doesn't see it, Kzenexplorer closes as soon as I start it.  One media player DOES see it, Banshee.  But there is no way to see any files or folders, except for playlists.  Also, I cant add or remove any files, since I cant see them.  I am pissed.

I have been looking for a solution for a long time.  Does anyone have any idea how to fix this?

Ubuntu 8.4, x64 
Dell DJ 2nd gen, 20 gig, MTP protocal i'm guessing

lsusb -v outputs the following

> Bus 002 Device 006: ID 041e:412f Creative Technology, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x041e Creative Technology, Ltd
  idProduct          0x412f 
  bcdDevice            1.00
  iManufacturer           1 Dell Inc
  iProduct                2 Dell DJ
  iSerial                 3 01012551AA03904B
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         16 Configuration 1
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface             33 MTP Interface
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
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
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
        bInterval               4
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
can't get debug descriptor: Connection timed out
Device Status:     0x0000
  (Bus Powered)


---

### Post by mattigras on 2009-02-04
Gnomad 2 works out of the box with my 20gb Dell DJ 2nd Gen. I downloaded it after viewing this thread and it just worked. I included the output of lsusb for comparison.


```
Bus 003 Device 007: ID 041e:4126 Creative Technology, Ltd Dell DJ (2nd gen)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x041e Creative Technology, Ltd
  idProduct          0x4126 Dell DJ (2nd gen)
  bcdDevice            0.01
  iManufacturer           1 Creative Technology
  iProduct                2 Dell DJ
  iSerial                 3 0101255127038C50
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Media
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5
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
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

