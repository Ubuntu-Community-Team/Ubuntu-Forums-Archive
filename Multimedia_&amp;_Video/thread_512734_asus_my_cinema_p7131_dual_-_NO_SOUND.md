---
title: "asus my cinema p7131 dual - NO SOUND"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by brainformat on 2007-07-29
hi! i have tv card form the title instaled on my ubuntu 7.04 comp.
it works fine with tvtime, but with no sound. i have googled for a month, but haven't found any answer that helped. 

possible solution might be in Restricted Drivers Manager where i have "v4l2-int-device" enabled but not in use. i can't figure up how to put it in use.

thanx a lot!

---

### Post by brainformat on 2007-07-31
someone, help me! :(

---

### Post by Hugolp on 2007-08-10
I get the same module (v4l2-int-device) in restricted modules and it never gets in use as well. I get it only when I load kernel 2.6.20-16. When I load kernel 2.6.20-15 it doesnt appear.

Also, I have problems with two webcams that dont work in kernel -16 but do in kernel -15. And both camera use diferent drivers, and both wont work in -16, but do in -15.

So you are having problems with a video card and I am having troubles with two video cams and we both get this "v4l2-int-device". v4l2 stands for video for linux 2 so I guess theres a bug in the new packages. 

What I am doing now is sticking with kernel 2.6.20-15 until this problem is solved. I suggest you try to reboot and load with kernel 2.6.20-15 and check if that way it works.

Hugo

---

### Post by startherepodcast on 2007-10-23
Maybe This Will Help: [http://ubuntuforums.org/showthread.php?t=497627&highlight=p7131]("http://ubuntuforums.org/showthread.php?t=497627&highlight=p7131")

---

