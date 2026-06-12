---
title: "Webcam"
date: 2010-01-03
forum: Multimedia Software
---

### Post by evilgizmo on 2010-01-03
Greetings,

First of all, sorry for my bad English. :)

I have difficulties with my Webcam. For the first time it tried to connect one on Linux. The camera is a Logitech C200. Google told to me, that I need the UVC driver. After setting up the driver, I checked the camera with the **luvcview** command. Everything is working. When I'm closing the camera window and executing the **luvcview** command again, then I get this answer:

[B]evilgizmo@ubuntu:~$ luvcview
luvcview version 0.2.1
Video driver: x11
A window manager is available
video /dev/video0
Unable to set format: 5.
Init v4L2 failed !! exit fatal[/B]

And what's next? If I reboot the PC, then everything is working again. In other forums was the recommendation to switch the camera to another USB, but then I got this error:

[B]evilgizmo@ubuntu:~$ luvcview
luvcview version 0.2.1
Video driver: x11
A window manager is available
video /dev/video0
ERROR opening V4L interface
: No such file or directory[/B]

After searching the net for an answare I got nothing. I did add the camera entry to the Skype configuration file what resulted in having the possibility to make video calls more then once per reboot, but the problem is still there.

So, what would be your suggestions for solving this problem? I hope you did understand me. :) If no then let me know and I will try to explain it some how :)

Some info:

Ubuntu Hardy (32-bit)
2.6.24-26-generic

ATI Radeon r200
Dell inspiron 1501

**lsbus**

Bus 006 Device 002: ID 046d:0802 Logitech, Inc.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

---

### Post by evilgizmo on 2010-01-04
*bump*

---

### Post by evilgizmo on 2010-01-05
Anyone?

---

### Post by evilgizmo on 2010-01-05
?

---

### Post by evilgizmo on 2010-01-08
I discovered, that no USB port is working after the webcam crashes. Is there a way to restart the USB ports? Some daemon for USB or so?

---

