---
title: "YPCendoscope - endoscope not showing in Cheese"
date: 2021-06-30
forum: Multimedia Software
---

### Post by fanofyes on 2021-06-30
I have a USB enscope that is not recognized by the Cheese app. Here is what I see from LSUSB:
```
06: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: DlBy.qcQdAXk2x2D
  Parent ID: uIhY.Iij6smqB8J2
  SysFS ID: /devices/pci0000:00/0000:00:1c.4/0000:05:00.0/usb3/3-2/3-2:1.1
  SysFS BusID: 3-2:1.1
  Hardware Class: unknown
  Model: "Sunplus Innovation YPCendoscope"
  Hotplug: USB
  Vendor: usb 0x1bcf "Sunplus Innovation Technology Inc."
  Device: usb 0x0b09 "YPCendoscope"
  Revision: "8.03"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Speed: 480 Mbps
  Module Alias: "usb:v1BCFp0B09d0803dcEFdsc02dp01ic0Eisc02ip00in01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (Hub)



```

What can I do to make it recognized by Cheese?

Thx.

---

### Post by fanofyes on 2021-06-30
I should add that I'm not so much interested in having Cheese recognize it than I am in being able to capture a video stream.

---

### Post by QIII on 2021-06-30
fanofyes --

Please enclose all terminal commands and their output in code tags.  This preserves formatting and makes your posts easier to read.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by fanofyes on 2021-06-30
Now I'm wondering whether it's due to an old HP-DM4 laptop (2010 I think) that does not have USB 3.0 but only USB 2.0

---

### Post by fanofyes on 2021-06-30
Nevermind, I figured it out: using ffmpeg allows me to detect the device.

---

