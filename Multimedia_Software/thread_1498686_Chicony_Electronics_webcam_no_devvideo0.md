---
title: "Chicony Electronics webcam no /dev/video0?"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Yeeha on 2010-06-01
Although my webcam is identified. I cant get my webcam to work. gstreamer-properties complains - Video for Linux 2 (v4l2): Cannot identify device '/dev/video0' when testing. I have installed packages suggested by sticky. Any suggestions?

---

### Post by van_Zeller on 2010-06-07
Same here...

Here is my lsusb output:

```
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 021: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

cheese shows no picture, skype as well. The video4linux control panel shows just a green screen. Camorama "says could not connect to video device".

Any thoughts? Thank you

---

