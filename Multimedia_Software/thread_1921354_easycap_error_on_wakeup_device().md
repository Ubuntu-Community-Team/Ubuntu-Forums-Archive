---
title: "easycap error on wakeup_device()"
date: 2012-02-06
forum: Multimedia Software
---

### Post by johannesgj on 2012-02-06
ive received the following error many times keeping me from using my (as of ubuntu 11.10 ) supported usb video grabber easycap.

heres first lsusb:
```
Bus 001 Device 003: ID 05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device

```

heres ls /dev/video*
```
 ls /dev/video*
/dev/video1
```

heres some of the output of dmesg:

```
[ 1259.284444] easycap::0adjust_brightness: adjusting brightness to  0x7F
[ 1259.285865] easycap::0adjust_contrast: adjusting contrast to  0x3F
[ 1259.287241] easycap::0adjust_saturation: adjusting saturation to  0x2F
[ 1259.288495] easycap::0adjust_hue: adjusting hue to  0x00
[ 1259.294656] easycap::0easycap_usb_probe: registered with videodev: 1=minor
[ 1259.294659] easycap::0easycap_usb_probe: ends successfully for interface 0
[ 1259.295487] easycap:: easycap_open: ==========OPEN=========
[B][ 1259.295721] easycap::0easycap_open: ERROR: wakeup_device() rc = -32
[ 1259.295723] easycap::0easycap_open: ERROR: wakeup_device() rc = -32[/B]
[ 1259.302262] usbcore: registered new interface driver snd-usb-audio
[ 1259.302404] usbcore: registered new interface driver easycap

```

its sad since everything makes me think the driver is running good enough but resulting in a srange error i havent been able to find on the internets.

bonus and maybe crucial info is that im running ubuntu in a vm in paralels on new 201 macbook.

---

