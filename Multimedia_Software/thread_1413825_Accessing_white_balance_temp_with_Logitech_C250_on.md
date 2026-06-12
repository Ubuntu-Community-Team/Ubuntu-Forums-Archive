---
title: "Accessing white balance temp with Logitech C250 on Ubuntu 9.10"
date: 2010-02-22
forum: Multimedia Software
---

### Post by kjaxatmit on 2010-02-22
Hi,

I am unable to access the "White Balance Temperature" control when I use my Logitech C250 in Ubuntu 9.10 (kernel version 2-6-31)

lsusb lists the following for the device: (full output attached)



Bus 001 Device 007: ID 046d:0804 Logitech, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0804 
  bcdDevice            0.09
  iManufacturer           0 
  iProduct                0 
  iSerial                 2 41D10170
  bNumConfigurations      1
 [...]
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier      16384
        bControlSize            2
        bmControls     0x0000175b
          Brightness
          Contrast
          Saturation
          Sharpness
          **White Balance Temperature**
          Backlight Compensation
          Gain
          Power Line Frequency
[...]

Every other client does not recognize this option is available. (uvcdynctrl, luvcview, v4l2-ctl)

However, I can successfully see this option when I am using Ubuntu 9.04 (kernel version 2-6-28)


It's appearing that there's some difference in the kernel between the two that's affecting the availability of the camera controls.

Help please? It's for a robotics vision application, so I need to be able to turn off the auto wb features but still have control over the white balance levels.

Thanks!

---

