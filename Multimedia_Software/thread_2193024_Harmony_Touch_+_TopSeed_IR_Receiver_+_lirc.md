---
title: "Harmony Touch + TopSeed IR Receiver + lirc"
date: 2013-12-10
forum: Multimedia Software
---

### Post by walth on 2013-12-10
I can see keypresses when I use mode2 but I get nothing with irw or irrecord.  I'm at a loss for where to go at this point and am hoping someone has some tips.

lsusb -v
```

Bus 001 Device 003: ID 1784:0011 TopSeed Technology Corp. eHome Infrared Transceiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1784 TopSeed Technology Corp.
  idProduct          0x0011 eHome Infrared Transceiver
  bcdDevice            1.00
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
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1

```

Remote Section of /etc/lirc/hardware.conf, Transceiver is set to none
```

REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/event3"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

```

lircd.conf points to /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

Here is the output from mode2 after hitting a key which I assume means it's receiving as expected.
```

root@kerby:/etc/lirc# mode2 -d /dev/lirc0 
space 16777215
pulse 4950
space 4850
pulse 850
space 1650
pulse 900
space 1650
pulse 850
space 1700
pulse 800
space 850
pulse 850
space 1700
pulse 850
space 1650
pulse 850
space 1700
pulse 850
space 4450
pulse 900
space 800
pulse 850
space 850
pulse 850
space 800
pulse 900
space 800
pulse 850
space 850
pulse 850
space 800
pulse 850
space 1700
pulse 850
space 850
pulse 1700
space 800
pulse 850
space 1700
pulse 850

```

Invoking 'irw' gives me nothing when hitting keys.  I see the remote light up and the receiver light up when buttons are hit.

Does anyone have any suggestions or an update to date guide?  I've been searching for a couple of days now and would like to check this off my list.

Thanks for any help.

---

### Post by walth on 2013-12-11
I read that lirc is no longer necessary and when I uninstalled it the arrow keys started working.  However I'm still having issues getting anything else to work in XBMC.  Trying to mess with ir-keytable to see if I can figure something out.

---

