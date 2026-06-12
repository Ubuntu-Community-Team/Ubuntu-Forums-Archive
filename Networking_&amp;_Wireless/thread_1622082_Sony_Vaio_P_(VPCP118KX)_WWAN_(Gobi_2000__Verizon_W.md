---
title: "Sony Vaio P (VPCP118KX) WWAN (Gobi 2000 / Verizon Wireless) not appearing on 10.04"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by quinthar on 2010-11-15
Hi!  Can you help me get the WWAN driver to appear under 10.04 on my Vaio P?

(Note: There are several other threads on similar topics, but so far as I can tell they're referring to different models or something different, as I can't get their suggestions to work.  Does anybody have the exact model I'm listing above?)

The problem: I installed 10.04 on the Vaio P and it works mostly great out of the box, except the WWAN module either doesn't appear, or only appears erratically after booting into Windows 7.  The most promising solution was listed here:

[INDENT][http://ubuntuforums.org/showthread.php?t=1478684&highlight=vaio](http://ubuntuforums.org/showthread.php?t=1478684&highlight=vaio)[/INDENT]

But it just didn't do anything.  These links seem to have a lot of good details, but they don't appear to be for the exact hardware I have and  I'm concerned they'll break everything:

[INDENT][http://www.madox.net/blog/2010/01/06/hp5310m-un2420-wireless-gobi2000-module-in-ubuntu/](http://www.madox.net/blog/2010/01/06/hp5310m-un2420-wireless-gobi2000-module-in-ubuntu/)
[http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html](http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html)[/INDENT]

I'm really bummed and would appreciate any help you can offer.  The relevant part of lsusb is below:

```
Bus 001 Device 003: ID 05c6:9224 Qualcomm, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05c6 Qualcomm, Inc.
  idProduct          0x9224 
  bcdDevice            0.02
  iManufacturer           3 Qualcomm Incorporated
  iProduct                2 Qualcomm Gobi 2000
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          1 Qualcomm Configuration
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
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

So note: lsusb *does* show the device, even though it *does not* show up when I click the network icon in the system tray.  Can you point me in the right direction, or adapt/condense any of the instructions from the links to something that might work for me?  Thanks!

-david

---

