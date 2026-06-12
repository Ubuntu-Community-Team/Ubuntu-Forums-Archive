---
title: "Sveon STV22"
date: 2010-04-20
forum: Mythbuntu
---

### Post by c1ru on 2010-04-20
Hi all people.
I just buyed that new card .
[http://www.sveon.com/fichaSTV22.html](http://www.sveon.com/fichaSTV22.html)

The only i can now is that card uses afatech chipset but i dont know model.

What can i do or watch for look and find one driver?

On logs i dont find any specific about dvb or usb.

Thank you, and apologyze about my english.

---

### Post by c1ru on 2010-04-20
I just tested under windows and media center says detected af9015 bda filter #1 and #2
But i have anothers adapters with chipset af9015 and is detected fast under ubuntu,

---

### Post by klc5555 on 2010-04-20
> **c1ru said:**
> I just tested under windows and media center says detected af9015 bda filter #1 and #2
But i have anothers adapters with chipset af9015 and is detected fast under ubuntu,

Not an adapter I would want to try to use, but with an af9015 chipset you may wish to start here:  [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444)

Also the problem with this tuner has popped up once before on this forum, with some progress made, but no definitive solution. See [http://ubuntuforums.org/showthread.php?p=9073493](http://ubuntuforums.org/showthread.php?p=9073493)

---

### Post by c1ru on 2010-04-20
I really HATE that chipset.

And all adapters now have that chipset.

here is more info:

> Bus 001 Device 003: ID 1b80:e401 Afatech 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b80 Afatech
  idProduct          0xe401 
  bcdDevice            2.00
  iManufacturer           1 AG Sistemas Informaticos
  iProduct                2 SVEON STV22
  iSerial                 0 
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
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
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


---

### Post by c1ru on 2010-04-21
> **klc5555 said:**
> Not an adapter I would want to try to use, but with an af9015 chipset you may wish to start here:  [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444)

Also the problem with this tuner has popped up once before on this forum, with some progress made, but no definitive solution. See [http://ubuntuforums.org/showthread.php?p=9073493](http://ubuntuforums.org/showthread.php?p=9073493)

I dit it and on dmesg | grep dvb i have nothing.
On lsusb:
Bus 002 Device 004: ID 1b80:e401 Afatech

---

