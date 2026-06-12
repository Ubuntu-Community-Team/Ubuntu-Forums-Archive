---
title: "[SOLVED] Remote help..."
date: 2007-11-16
forum: Mythbuntu
---

### Post by bmturney on 2007-11-16
Installed Mythbuntu a few days ago and so far I really like it... but to say I'm a Linux/Myth Noob is an understatement, so please be gentle...

To get started with using Myth I'm just planning on using it to watch some videos that I have... not doing any TV stuff with it yet.  I got my video card working in Linux, got my videos loaded into Myth.. the only thing I have left before moving this bad boy into the living room is getting the remote to work.

The only remote I have right now is a Dell Remote to run MCE that was on a laptop that I bought about two years ago.  The remote is pretty basic, and has an IR receiver that plugs into a USB port.

When I installed Mythbuntu I told it that I was using a "Windows Media Center Remote (old version Microsoft USB)" but the remote does not seem to be working at all.  I would really like to use this remote if I could, at least for the time being... any help would be greatly appreciated.

Please remember... I'm a Linux noob, so I need details for most stuff...

---

### Post by road2elysium on 2007-11-17
> **bmturney said:**
> 

The only remote I have right now is a Dell Remote to run MCE that was on a laptop that I bought about two years ago.  The remote is pretty basic, and has an IR receiver that plugs into a USB port.

When I installed Mythbuntu I told it that I was using a "Windows Media Center Remote (old version Microsoft USB)" but the remote does not seem to be working at all.  I would really like to use this remote if I could, at least for the time being... any help would be greatly appreciated.



The "Windows Media Center remote (old version Microsoft USB)" is primarily for Microsoft branded MCE Remotes.  The Dell one might be one of the newer versions, i.e. the Windows Media Center remote (Philips, et. al).  Find out more here: [http://www.mythtv.org/wiki/index.php/MCE_Remote]("http://www.mythtv.org/wiki/index.php/MCE_Remote")

Most of the relevant information is in the upstream Mythtv wiki.  However, you'll want to start out by checking how your USB IR Receiver is recgonized by doing a:
```
lsusb
```
Using a verbose option might help here if you find out your remote isn't actually the mceusb2.

---

### Post by bmturney on 2007-11-17
here is the info from lsusb for this device... it looks like it isn't an actually an MCE device at all...  I looked on the MythTV wiki and I can't find anything pertaining to the Dell IR Remote.. any suggestions?

Bus 001 Device 007: ID 413c:2505 Dell Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x2505 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
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
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              5 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     190
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
        wMaxPacketSize     0x0005  1x 5 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

---

### Post by road2elysium on 2007-11-17
> **bmturney said:**
> here is the info from lsusb for this device... it looks like it isn't an actually an MCE device at all...  I looked on the MythTV wiki and I can't find anything pertaining to the Dell IR Remote.. any suggestions?

Bus 001 Device 007: ID 413c:2505 Dell Computer Corp. 
...
...
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0005  1x 5 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

If you sudo lsusb, you probably won't get the Unavailable/Operation not permitted issues.

As for the remote itself, if it's being recognized as a HID (Human Interface Device) you might want to check the /dev/input/events.  If you ```
sudo cat eventX
``` while pressing buttons on your remote, you should be able to tell which dev/input/event corresponds to your remote.

From there you should be able to follow standard lirc guides to fix your remote.

---

### Post by bmturney on 2007-11-17
I got the remote to work... (lirc apprently wasn't installed... ) the only thing left to do now is map the buttons I guess... 

Thanks for the help... it did help quite a bit...

---

### Post by road2elysium on 2007-11-18
> **bmturney said:**
> I got the remote to work... (lirc apprently wasn't installed... ) the only thing left to do now is map the buttons I guess... 

Thanks for the help... it did help quite a bit...

Congratulations.  When you finish mapping the buttons and creating a sane lircrc/lircd/hardware.conf, you can contribute those to the lirc project/mythbuntu-lirc-generator.

---

