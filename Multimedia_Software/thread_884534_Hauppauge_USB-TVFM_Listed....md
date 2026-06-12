---
title: "Hauppauge USB-TVFM Listed..."
date: 2008-08-09
forum: Multimedia Software
---

### Post by dchurch24 on 2008-08-09
...but I don't know how to use it.

When I do a lsusb I get this:

```

Bus 001 Device 008: ID 0573:4d32 Zoran Co. Personal Media Division (Nogatech) Hauppauge WinTV-USB III (PAL) FM Model 573
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0573 Zoran Co. Personal Media Division (Nogatech)
  idProduct          0x4d32 Hauppauge WinTV-USB III (PAL) FM Model 573
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      4

```

So I know the device is there and recognised, but I don't know where it's mounted, or even if I have to mount it manually, or even at all.

There's nothing in /dev/Video0 or /dev/Video1 - or at least not that I can tell.

I've tried using VLC to open both 0 and 1 but I get nothing.

Can anyone point me in the right direction please?

I'm sure it's close. I want to be able to use my old analogue camcorder, and I used to use this device to get the output to the computer. Also, I have some wireless cameras that I could use as a sort of door entry system.  I also have a Nova-T PCI card in the box too, but I can't get that to see the analogue stuff.

Thank you in advance.

EDIT: now a /dev/video2 has appeared, but I still can't get any output.

---

