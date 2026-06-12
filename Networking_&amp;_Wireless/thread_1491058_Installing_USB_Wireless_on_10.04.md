---
title: "Installing USB Wireless on 10.04"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by sloterhouse5 on 2010-05-23
Just installed 10.04 but can't seem to get wireless working.  Fry's brand USB device (FR-54USB). Device works when booted to Windows but light never comes on in Ubuntu so I'm guessing it's a driver issue.  Bit of a noob here, sorry.

It looks like this is a D-Link chipset but I can't tell which one.  lsusb shows the following:

Bus 001 Device 005: ID 07d1:3305 D-Link System 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x07d1 D-Link System
  idProduct          0x3305 
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
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
:

---

### Post by chili555 on 2010-05-23
It has a Realtek 8192su chipset. Do you have System > Administration > Windows Wireless Drivers? You can probably get it working with these files I have attached. Download the file to your desktop, right click and select Extract Here. Then open System > Administration > Windows Wireless Drivers and navigate to Desktop > X86 and let it install the net8192su.inf. It will need and grab the rtl8192su.sys file at the same time. You should be all set.

---

### Post by sloterhouse5 on 2010-05-23
The Realtek 8192su drivers worked.  Thanks much!!

---

### Post by chili555 on 2010-05-23
> **sloterhouse5 said:**
> The Realtek 8192su drivers worked.  Thanks much!!Great work. I think you can discard the noob status now.

---

### Post by tweaked on 2010-05-23
Chili, I am going through the same thing but I do not have System > Administration > Windows Wireless Drivers listed. is there another way to get thes loaded?

Thanks

edit: Got it and it works.  THANKS!!!

---

### Post by Slave2Metal on 2010-05-23
> **tweaked said:**
> Chili, I am going through the same thing but I do not have System > Administration > Windows Wireless Drivers listed. is there another way to get thes loaded?

Thanks
You need to install ndiswrapper from the repositories.

---

### Post by wuffeemoz on 2010-06-10
Hi so i had 9.10 and i bought this wireless card because it was the cheapest it didn;t work so i didn't use ubuntu. then i found this thread a few months later and i tryed the wireless thing. it didn't work. so then i updated to 10.04 and did the same thing. it didn't work. any help for a lazy noob?

---

### Post by chili555 on 2010-06-10
Did you install the driver in Windows Wireless Drivers? What does this say?```
ndiswrapper -l
```Thanks.

---

### Post by wuffeemoz on 2010-06-10
it says device present. could it be that i have another wireless card in (i'm borrowing it to do this stuff)? thanks in advance

---

### Post by chili555 on 2010-06-10
> could it be that i have another wireless card in I'm sure that I don't know. Do you see a Fry's brand USB device (FR-54USB) sticking out? You can find out what device you have with:```
lsusb
```If it's not the same, ID 07d1:3305 D-Link System, then I am wondering why you tagged on to this thread and installed the wrong driver.

---

### Post by wuxia1911 on 2010-06-21
I got this working but it only works on WPA, not on WEP. Is there any way to fix this? I read somewhere else that you might need to type some stuff in the terminal to make it work on WEP. Can anyone confirm this?

---

### Post by mojo6911 on 2011-03-05
I downloaded the file from the manufacturer:

[http://www.frysnetworksupport.com/Product/View.aspx?ProdID=6](http://www.frysnetworksupport.com/Product/View.aspx?ProdID=6)

Running 10.10 64 bit and installed ndiswrapper. When I still the WinXP x64 drivers, ndiswrapper both in the command line and gui freeze up. The 32 bit drivers don't work for me.

---

