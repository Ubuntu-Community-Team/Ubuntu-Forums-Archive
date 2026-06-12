---
title: "labtec 1200 in ubuntu 9.10"
date: 2010-03-05
forum: Multimedia Software
---

### Post by Turiko on 2010-03-05
I have tested this webcam with cheese, and it is able to take pictures and record video. However, the screen is pitchblack when previewing.

user@GIPbak:~$ lsusb
Bus 004 Device 005: ID 093a:2464 Pixart Imaging, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0425:0101 Motorola Semiconductors HK, Ltd G-Tech Wireless Mouse & Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1624 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The webcam is detected as an usb device, but previewing doesn't work. I want to use this webcam with zoneminder, and zoneminder requires the preview to work.

Does anyone have any advice? I've looked around quite a bit, but i can't find any specific fix. I did find a .patch file, but i have no idea how to implement it.

---

### Post by Turiko on 2010-03-05
bump, anyone?

---

### Post by T3kG33k on 2010-03-30
I've been looking and I haven't found much myself.  I'll reply back here if I do.

---

### Post by no2498 on 2010-03-31
open cheese click edit prefernce
see if setting pic to a smaller size helps any
cheese does have a nice help file

---

