---
title: "Genius VideoCam Look problems"
date: 2008-07-30
forum: Multimedia Software
---

### Post by hujer on 2008-07-30
When starts my Ubuntu 8.04 successfully detects USB web camera Genius VideoCam Look. It even puts on the front light on camera, but the camera itself does not work. Below there are relevant listings of lsusb ane dmesg. The only problem I can see is the message: "Optional device control through 'sysfs' interface disabled". Please could anybody help me to make the camera work before I shall throw it away from my window and go to buy another one, surely working on Ubuntu?

lsusb
...
Bus 001 Device 003: ID 0c45:60b0 Microdia Genius VideoCam Look

dmesg
...
[   44.326038] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
[   44.328104] usb 1-3: SN9C103 PC Camera Controller detected (vid:pid 0x0C45:0x60B0)
...
[   44.628942] usb 1-3: OV7630 image sensor detected
[   45.045945] usb 1-3: Initialization succeeded
[   45.045987] usb 1-3: V4L2 device registered as /dev/video1
[   45.045990] usb 1-3: Optional device control through 'sysfs' interface disabled
...
[   45.046015] usbcore: registered new interface driver sn9c102

Thank You.

---

### Post by DapperDrakeNewbieDR on 2008-08-04
> **hujer said:**
> When starts my Ubuntu 8.04 successfully detects USB web camera Genius VideoCam Look. It even puts on the front light on camera, but the camera itself does not work. Below there are relevant listings of lsusb ane dmesg. The only problem I can see is the message: "Optional device control through 'sysfs' interface disabled". Please could anybody help me to make the camera work before I shall throw it away from my window and go to buy another one, surely working on Ubuntu?

lsusb
...
Bus 001 Device 003: ID 0c45:60b0 Microdia Genius VideoCam Look

dmesg
...
[   44.326038] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
[   44.328104] usb 1-3: SN9C103 PC Camera Controller detected (vid:pid 0x0C45:0x60B0)
...
[   44.628942] usb 1-3: OV7630 image sensor detected
[   45.045945] usb 1-3: Initialization succeeded
[   45.045987] usb 1-3: V4L2 device registered as /dev/video1
[   45.045990] usb 1-3: Optional device control through 'sysfs' interface disabled
...
[   45.046015] usbcore: registered new interface driver sn9c102

Thank You.

Same problem here.

---

### Post by DapperDrakeNewbieDR on 2008-08-04
> **DapperDrakeNewbieDR said:**
> Same problem here.

Actually, I just found out it's working fine for me with kopete.

---

### Post by ron262 on 2008-08-05
Hi,

Genius video cam Look problems. It's nice and attractive thred. it gives relevant informatrions about Videocam. I visit this site whenever I get time.

Ron
=============================================================
[http://www.treatmentcenters.org/louisiana](http://www.treatmentcenters.org/louisiana)

---

### Post by Kuzja on 2008-08-22
Have a look here guys [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/). There is already an experimental support for some microdia cameras. Join in to help build linux driver for microdia web cams.

---

