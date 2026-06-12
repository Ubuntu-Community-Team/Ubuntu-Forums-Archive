---
title: "need help with webcam in Edgy"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by nitewing98 on 2007-04-22
I've got an argus PC300 webcam and am trying to get it to work.  The light on the cam comes on, and dmesg seems to indicate the correct driver:
[17179609.316000] drivers/media/video/ov511/ov511.c: USB OV518+ video device found
[17179609.336000] drivers/media/video/ov511/ov511.c: Device revision 2
[17179609.384000] drivers/media/video/ov511/ov511.c: Compression required with OV518...enabling
[17179609.956000] drivers/media/video/ov511/ov511.c: Sensor is an OV7620
[17179611.096000] drivers/media/video/ov511/ov511.c: Device at usb-0000:00:07.4-1 registered to minor 0
[17179611.136000] drivers/media/video/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
[17193379.452000] drivers/media/video/ov511/ov511.c: No decompressor available

However, Camorama says "Cannot connect to video device (/dev/video0). Please check connection"

Any idea what's wrong?

---

### Post by Cueball696 on 2007-04-22
Well when you find out . please email me.. I get the same thing:"Cannot connect to video device (/dev/video0). Please check connection" . thanks


[email]Cueballnoc@gmail.com[/email]

---

### Post by nitewing98 on 2007-04-22
Don't know if it helps, but here are the 2 items listed in my /dev folder (that supposedly don't exist):

lrwxrwxrwx 1 root root        6 2007-04-22 14:21 /dev/video -> video0
crw-rw---- 1 root video 81,   0 2007-04-22 14:21 /dev/video0

Anyone have a cam that DOES work?  What do your entries look like?  Perhaps it is an ownership or permissions issue?

---

### Post by nitewing98 on 2007-04-24
OK, this is really annoying!  I can see the cam listed in device manager, it seems to be recognized by Easycam2 even, but I can't for the life of me get a bit of video!  Even the microphone on the thing is recognized by the sound manager, but no video output.

Please, if anyone has a cam that works (especially with the OV511 or OV51+ drivers), please post back and help me and Cueball out!

---

