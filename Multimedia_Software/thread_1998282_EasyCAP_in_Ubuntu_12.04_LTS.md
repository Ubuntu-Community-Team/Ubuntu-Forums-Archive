---
title: "EasyCAP in Ubuntu 12.04 LTS"
date: 2012-06-06
forum: Multimedia Software
---

### Post by tnob on 2012-06-06
Hi all,

On reading various mixed messages concerning EasyCAP, I can't find anything with respect to EasyCAP's functionality in Ubuntu 12.04 LTS. What are your experiences (if any)?

tnob

---

### Post by vapor216 on 2012-06-19
At least partly working for me, I need to test more to confirm how well it is working.  Haven't tried audio yet.  It looked promising at first plug-in, the easycap driver is in the kernel and it loaded, however all the viewing apps I tried froze until I applied the "bars=0" easycap kernel module option described here:
[http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html](http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html)

> 
[FONT=Courier New]Create a file: /etc/modprobe.d/easycap.conf[/FONT][FONT=Courier New]
Add:
options easycap bars=0[/FONT]
Also mentioned there, using v4l2-ctl (from the v4l-utils package) to set the input channel so that the device will work with other apps that don't allow you to change the input channel:
> 
v4l2-ctl -d /dev/video0 -i 0
On my device, 0 and 1 are for composite and 5 is for s-video input.

This at least works for me now with composite input:
```
mplayer tv:// -tv driver=v4l2:width=720:height=480:outfmt=uyvy:norm=NTSC_M:device=/dev/video0:input=1:fps=25 -vo sdl -nosound
```I have this device (from lsusb):
ID 05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device

---

