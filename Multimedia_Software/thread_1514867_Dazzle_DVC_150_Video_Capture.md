---
title: "Dazzle DVC 150 Video Capture"
date: 2010-06-21
forum: Multimedia Software
---

### Post by skaarr on 2010-06-21
OK, so I have a Dazzle DVC 150 external video capture device. It plugs in via usb. I would like to know if it is at all possible to get it working. It does not seem to be detected by any capture software (vlc etc). I have also tried running the software that came with it (Pinnacle Studio 9) in WINE but it can still not detect it, so I tried running Windows XP in Virtualbox, still no luck. (EDIT: realised Virtualbox doesn't have usb support, are there any similar programs that do?)

I would just like to know if there is anyway I can get the device working (and if you don't know how I'd still welcome recommendations of external capture devices that work with Ubuntu).

Any and all help appreciated, thanks.




Extra Info:

The device does appear (and is named) in the output of lsusb -v

```
Bus 002 Device 005: ID 2304:0205 Pinnacle Systems, Inc. [hex] DVC 150B
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2304 Pinnacle Systems, Inc. [hex]
  idProduct          0x0205 DVC 150B
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
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
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```If the output of dmesg is any use I can post it all up, but there are references to usb video: 
 
```
[   20.205588] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   20.205641] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   20.262317] [drm] Initialized drm 1.1.0 20060810
[   20.272202] Linux video capture interface: v2.00
[   20.301354] uvcvideo: Found UVC 1.00 device CNF8111 (04f2:b119)
[   20.306665] cfg80211: Calling CRDA to update world regulatory domain
[   20.311421] input: CNF8111 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input8
[   20.311481] usbcore: registered new interface driver uvcvideo
[   20.311484] USB Video Class driver (v0.1.0)

```

---

### Post by skaarr on 2010-06-22
Anyone? Any ideas?

---

### Post by skaarr on 2010-06-24
bump

---

### Post by skaarr on 2010-06-28
nothing? anyone even seen this post?

---

### Post by phatcartoon on 2010-07-09
I see this post, but I'm waiting just like you.  I have the same device, but haven't had any luck.  The only OSs installed at my house are Linux distros.  This little box just sits in the corner of my room.  Wish I could put it to some use.  Got some old skate footage I would like to transfer. . . I'll keep looking, but if you find a solution, please post.  I'll do the same.

Some one, please help us.  :)

---

### Post by no2498 on 2010-07-10
i have seen a few ? for " s-video "

hope thats what your looking for

---

