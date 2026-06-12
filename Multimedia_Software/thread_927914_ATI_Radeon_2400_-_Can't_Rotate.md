---
title: "ATI Radeon 2400 - Can't Rotate"
date: 2008-09-23
forum: Multimedia Software
---

### Post by pollian on 2008-09-23
ATI 2400 - Can't Rotate
I have a Dell desktop with the ATI Radeon HD 2400 XT running Hardy. The video card seems to be working fine, in general. I can change screen resolution, refresh rate, etc. But rotation isn't enabled. When I run xrandr, I get the following output.

> Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
1280x1024 75.0* 70.0 60.0
1280x960 60.0
1280x768 60.0
1152x864 75.0 70.0 60.0
1024x768 75.0 72.0 70.0 60.0
800x600 75.0 72.0 70.0 60.0 56.0
640x480 75.0 72.0 60.0
640x400 75.0 60.0
512x384 75.0 60.0
400x300 75.0 60.0
320x240 75.0 60.0
320x200 75.0 60.0


Is this something I can fix by changing xorg.conf? If so, can someone point me towards instructions?

pollian

 - I posted this in general help last week but since I didn't get any replies, I thought I'd try here

---

### Post by mike310z on 2008-10-27
I think this turns it on  
aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"

---

