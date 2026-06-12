---
title: "Creative Live! Cam Optia not working with messenging applications"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by yorost on 2007-08-25
I have a Creative Live! Cam Optia and it works fine using linux-uvc and the program luvcview.  However, I cannot get it to work with aMSN, Kopete, or Ekiga.  Google has helped me find some help, but I've been unable to get things to work.

---

### Post by jz_element on 2007-09-10
Hi,
Would you tell me know how you made this Creative Live! Came work with UVC and luvcview?
When I enter ./luvcview, I got this message

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

Do you know where is wrong?

I installed uvc driver by doing 'make' and 'sudo make install'. Is this right?
Thanks

Joe

---

### Post by YannickDefais on 2007-09-12
Hi,

Did you try Ekiga 2.0.9?
[https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c](https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c)

Regards,
Yannick

---

### Post by bluetooth on 2007-10-15
I tried Ekiga 2.0.9. I get first frame and then image stills. Trying to make my Optia to work in Ubuntu for a long time, no success so far...

---

### Post by YannickDefais on 2007-10-15
Hi, if it is this webcam:
[http://wiki.ekiga.org/index.php/Image:Live_cam_optia.jpg](http://wiki.ekiga.org/index.php/Image:Live_cam_optia.jpg)

Then you need to install ekiga 2.0.11:
[http://ekiga.org/index.php?rub=5](http://ekiga.org/index.php?rub=5)
with driver uvcvideo:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

It should work with 2.0.11

Regards,
Yannick

---

### Post by bluetooth on 2007-11-13
**YannickDefais**, thanks, I'm on Gutsy now. The webcam works without any additional software or drivers :)

---

### Post by YannickDefais on 2007-11-13
good

---

