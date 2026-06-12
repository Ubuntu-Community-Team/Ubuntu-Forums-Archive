---
title: "Logitech quickcam pro 5000 on ibex 64-bit"
date: 2009-01-11
forum: Multimedia Software
---

### Post by okey666 on 2009-01-11
I want to use my quickcam pro 5000 for a few programs (such as amsn, something to take pictures and videos...
 and stopmotion) and none of them will work. I seem to recall, sometime back in the old days of 6.* (or something like that) I got it to work using cheese, and possibly amsn, but I can't remember now.

lsusb:
> 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 1241:1503 Belkin Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


It is detected in amsn, it seems, but amsn crashes or just gives a blank screen. It is listed as UVC camera 1, so I presume that means I am using the UVC drivers? In Cheese, it seems to detect it but no image comes up and in stopmotion it either crashes or gives long strange errors.

It does work in one program, called motion, but that is only command line, and only takes pictures (it is designed for motion  detection). I have linked motion to stopmotion which gives me a video feed, but when I press the "take picture" button stopmotion crashes.

Could anyone help? I am using 8.10 64-bit

---

### Post by kaivalagi on 2009-01-11
I have the same web cam and dont have it working either.

I had it working with Gutsy some time ago, but I cant remember what I did, I think I had to build v4l2 from scratch and modprobe it in if I remember correctly.

I'd be interested to know how to get it working in Ibex...especially if it means just fiddling with config settings rather than compiling drivers...

edit: I think I just compiled uvcvideo.ko before and modprobed, tried it again and it doesn't help at all.....

---

### Post by okey666 on 2009-01-17
Well... due to a problem that I will not go into, I had to reinstall Ibex. Hoping that this would fix my cam, I went for 32bit. No such luck, I think it is because it is v4l2.

---

### Post by okey666 on 2009-01-22
bump (can you bump on these forums??)

---

### Post by kaivalagi on 2009-01-22
You can **bump** within moderation :)

---

### Post by okey666 on 2009-02-01
> **kaivalagi said:**
> You can **bump** within moderation :)
thanks...

Today I used tbeta (a multi touch screen program, very good try it!) with my web cam, and that worked fine, it did not even need any configuration, it just worked...

It seems that there just are not any good programs that support v4l2.

---

### Post by okey666 on 2009-02-01
Just posted that, and then tried again. My webcam worked in cheese!! I guess thats this solved.

---

### Post by kaivalagi on 2009-02-01
I can confirm my web cam is working in cheese too, one of the recent updates must have fixed it :)

edit: Ekiga works too...

---

