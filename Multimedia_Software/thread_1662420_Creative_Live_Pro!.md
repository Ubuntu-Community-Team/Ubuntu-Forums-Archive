---
title: "Creative Live Pro!"
date: 2011-01-08
forum: Multimedia Software
---

### Post by adduds on 2011-01-08
Hi there :) 

I installed skype and can't seem to use the webcam upon further investigation I have actually yet to find instructions on how to use my webcam on linux; i have a Creative VF 0080

i tried

gstreamer-properties

when changing plugin from Linux 2(v4l2) or (v4l) i get this error

```
Video for Linux (v4l): Device "/dev/video0" does not exist.
```

my cams recognized.....

```
toews@desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0fca:8004 Research In Motion, Ltd. 
Bus 001 Device 004: ID 1058:0705 Western Digital Technologies, Inc. 
[COLOR="Red"]Bus 001 Device 003: ID 041e:4038 Creative Technology, Ltd ORITE CCD Webcam [PC370R][/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

also downloaded and installed cheese says

"No device found"

Any help would be greatly appreciated!!! :) TY

---

### Post by adduds on 2011-01-09
bump

---

### Post by adduds on 2011-01-10
k honestly...can someone help? i posted this like 2-3 days ago...

---

### Post by adduds on 2011-01-11
> **adduds said:**
> k honestly...can someone help? i posted this like 2-3 days ago....

---

### Post by adduds on 2011-01-17
It is recognized


lsusb:

Bus 001 Device 003: ID 041e:4038 Creative Technology, Ltd ORITE CCD Webcam [PC370R]


unplugging it and plugging it in...

dmesg:

[97449.210045] usb 1-2: new high speed USB device using ehci_hcd and address 4

Found this site:

EDIT:

[http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html)

WebCam Live! Pro VF0080 0x041e 0x4038

perhaps its just not supported?

---

### Post by adduds on 2011-01-21
still here

---

