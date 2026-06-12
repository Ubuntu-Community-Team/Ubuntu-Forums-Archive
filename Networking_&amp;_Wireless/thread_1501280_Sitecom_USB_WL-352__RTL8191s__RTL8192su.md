---
title: "Sitecom USB WL-352 / RTL8191s / RTL8192su"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by polopete on 2010-06-04
hi, i have looked threw the forum and found things similar to this but not the same as most point to PCI cards not USB,   i have been using Ubuntu 9.04 64bit for ages now but still have not gotten my wireless USB device to work / turn on, i have read a lot of tutorials about the 8191s chip-set and have tried lots of different ways to get it to work, including Ndiswrapper,  i gather that 64bit is harder to get wireless to work so i have now got Ubuntu 9.04 32bit installed and am going to try from here,  i just would like some help.......  

Ubuntu detects the device when i lsusb as shown here:  

lsusb -v output for wireless device

Bus 001 Device 004: ID 0df6:004c Sitecom Europe B.V. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0df6 Sitecom Europe B.V.
  idProduct          0x004c 
  bcdDevice            2.00
  iManufacturer           1 Manufacturer Realtek 
  iProduct                2 RTL8191S WLAN Adapter 
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
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
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0d  EP 13 OUT
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


but thats about as far as i get,  on 64bt 9.04 i also detected somewhere that the card was also rtl8192su and windows also reports it back as that, so what i hoping for is a little advice on what to do and if it is indeed possible to run this wireless USB device on Ubuntu and maybe better news would be that it also works on 64bit editions too. 

Please ask if you would like any more terminal output's of stuff and i will happy post away,  thanks,  polopete a.k.a pete wyatt.

---

### Post by polopete on 2010-06-06
After going back to 9.04 32 edition,  and without installing any updates,  i installed NDISWRAPPER,  used the windows xp driver which came on disk and Hay whalla working wireless network,  i did also install the RTL8191SU driver from realtek but that didnt do squat....   well guys thanks for your help... or lack of :D

---

