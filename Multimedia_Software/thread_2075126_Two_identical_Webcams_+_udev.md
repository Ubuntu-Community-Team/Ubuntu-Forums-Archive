---
title: "Two identical Webcams + udev"
date: 2012-10-23
forum: Multimedia Software
---

### Post by creiss on 2012-10-23
Hey folks,

I have a notebook with a fixed cam (ignore that) and two additional webcams (identitals) attached to it. On bootup there is a race condition where the fight for /dev/video1 and /dev/video2 begins. Sometimes the order is switched, making webcam photos a living hell.

I need camera 1 to always go to video1 (with sound enabled) and camera 2 to go to video2 (with sound disabled).

lsusb:
```

Bus 001 Device 015: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 016: ID 046d:0825 Logitech, Inc. Webcam C270

```

lsusb -v:
```

Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0825 Webcam C270
  bcdDevice            0.10
  iManufacturer           0 
  iProduct                0 
  iSerial                 2 E995D900
  bNumConfigurations      1

Bus 001 Device 016: ID 046d:0825 Logitech, Inc. Webcam C270
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0825 Webcam C270
  bcdDevice            0.10
  iManufacturer           0 
  iProduct                0 
  iSerial                 2 9286F810
  bNumConfigurations      1

```

My baked up udev-rule:
```

SUBSYSTEMS=="usb",ATTRS{serial}=="E995D900",SYMLINK+="facecam", NAME="video1"
SUBSYSTEMS=="usb",ATTRS{serial}=="9286F810",SYMLINK+="uggcam", NAME="video2"

```

So very not working. I get the device nodes but no sound on both, and if i unplud cam 1, the video link /dev/video1 still remains. I also get this in the syslog:

```

Oct 23 09:46:23 eulie udevd[3941]: kernel-provided name 'snd/pcmC3D0c' and NAME= 'video1' disagree, please use SYMLINK+= or change the kernel to provide the proper name
Oct 23 09:46:23 eulie udevd[3998]: kernel-provided name 'input/event18' and NAME= 'video1' disagree, please use SYMLINK+= or change the kernel to provide the proper name
Oct 23 09:46:23 eulie udevd[3997]: kernel-provided name 'snd/controlC3' and NAME= 'video1' disagree, please use SYMLINK+= or change the kernel to provide the proper name
Oct 23 09:58:18 eulie udevd[535]: kernel-provided name 'snd/pcmC3D0c' and NAME= 'video2' disagree, please use SYMLINK+= or change the kernel to provide the proper name
Oct 23 09:58:18 eulie udevd[537]: kernel-provided name 'snd/controlC3' and NAME= 'video2' disagree, please use SYMLINK+= or change the kernel to provide the proper name
Oct 23 09:58:18 eulie udevd[538]: kernel-provided name 'input/event18' and NAME= 'video2' disagree, please use SYMLINK+= or change the kernel to provide the proper name

```

I thought this would be a simple udev-fix, but ugh...

Any help would be greatly appreciated!
Cheers!
-Christian.

---

### Post by creiss on 2012-10-24
*shameful bump*

---

