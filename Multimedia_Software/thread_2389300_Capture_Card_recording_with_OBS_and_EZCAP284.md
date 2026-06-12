---
title: "Capture Card recording with OBS and EZCAP284"
date: 2018-04-14
forum: Multimedia Software
---

### Post by zhongtiao1 on 2018-04-14
I am trying to get my ezcap284 capture card to work on Ubuntu Kylin 16.04 using OBS. However, it is not recognized as a capture device by Ubuntu. It uses the IT9910HD driver on Windows if that helps.

This is the lsusb output:
```
Bus 001 Device 007: ID 048d:0281 Integrated Technology Express, Inc.
```

Here is the dmesg output:
```
[  914.192391] usb 1-1.3: new high-speed USB device number 12 using ehci-pci
[  914.355130] usb 1-1.3: New USB device found, idVendor=048d, idProduct=0281
[  914.355133] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  914.355136] usb 1-1.3: Product: ezcap
[  914.355137] usb 1-1.3: Manufacturer: www.ezcap.com

```

I do not know where it is mounted (if it even is) and VLC and OBS do not recognize it.

I would really prefer to use this instead of booting into windows every time I want to use it. Especially since I use Ubuntu Kylin far more often than Windows.

---

### Post by TheFu on 2018-04-15
A video device wouldn't be "mounted" - is would need the correct driver which would create a **v4l2** device which **obs** would see and use. Did a quick google for the device ID and linux ... didn't find any mention.  Does the vendor provide Linux drivers?  That would be where I started.

Is there some other program that works with this device on Linux?
Is there a /dev/vid[0-9] device?  I think that's the normal name given to video-4-linux devices.

---

### Post by zhongtiao1 on 2018-04-15
> **TheFu said:**
> A video device wouldn't be "mounted" - is would need the correct driver which would create a **v4l2** device which **obs** would see and use. Did a quick google for the device ID and linux ... didn't find any mention.  Does the vendor provide Linux drivers?  That would be where I started.

Is there some other program that works with this device on Linux?
Is there a /dev/vid[0-9] device?  I think that's the normal name given to video-4-linux devices.

To my knowledge there aren't any linux drivers, I have emailed the company asking about it, but they haven't responded (and I doubt they will). There is no /dev/vid[0-9] device.

---

### Post by TheFu on 2018-04-15
If there aren't drivers, then it won't work.  Not all ezcap devices are supported, but 3 are.  It appears this one doesn't have any Linux support.

---

### Post by alexandrexavier on 2018-04-16
There's no IT9910 driver in the Linux kernel yet. If you don't mind, can you open the device and take a pictures of the chips that it's using on the inside? We'd need to identify the chips that it's using. Eventually, if a driver is added, we can match the configuration of the Ezcap284 and add the USB ID 048d:0281 so it will be detected. I can't see the specs of the internals of this device when searching online.

---

