---
title: "video4linux support"
date: 2010-05-28
forum: Multimedia Software
---

### Post by lo.j on 2010-05-28
hello everyone.

i'd like to use my webcam, inside and outside the browser (chromium), so i guess i need v4l support.

what is the proper way to enable it?
- add "v4l1_compat" to /etc/modules
- add "modprobe v4l1_compat" to /etc/rc.local
- add "export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" on .bachrc
- else?

and... once loaded at boot, it is not necessary to type "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so chromium-browser" every time, right?

thanks.

---

### Post by no2498 on 2010-05-28
have you tried  to open the cam in cheese webcam booth

910 and up cheese should be loaded
look in sound & video

if the cam does not come on try this

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

hope this helps

as for the other stuff same as for skype

---

### Post by lo.j on 2010-05-28
hi and thanks for your answer.

my webcam is working quite good;
i'd just like to know how to load the driver at boot and the best way to get it working with chromium... if something else is needed instead of ld_preloading the driver each time i start the browser...

thanks.

---

### Post by no2498 on 2010-05-28
if thats the driver you use that should work

you can also preload it for other programs

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so   what ever name you need to use

put it in the same folder

hope that helps

---

