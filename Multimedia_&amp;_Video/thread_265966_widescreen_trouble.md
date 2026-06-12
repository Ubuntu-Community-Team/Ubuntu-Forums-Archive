---
title: "widescreen trouble"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by Strannik on 2006-09-26
Hello Gentlemen, I am having this problem with my Fujitsu siemens w19-1 monitor. It has a native resolution of 1440x900. It works fine under Windows and FreeBSD 6.1. I tried Ubuntu a while ago and then moved on to FreeBSD. When dapper came along, I wanted to try it out and finaly found the time. One big show stopper - i'm stuck in 1024x768. i searched the forum and internet for all the info i could find about nvidia drivers in ubuntu and tried two methods: installing the nvidia drivers with apt and by downloading the official drivers from nvidia.com. I get the same result from both of them:
1440x900 is accepted by the X server (as seen in the log file which i have attached) but the monitor falls back to 1152x870 (thats what it shows on its OSD) and the image is all smugged no matter how i ajust the settings. What can be done to get it working normally?

btw I'm using up2date dapper.

---

### Post by Strannik on 2006-09-27
Can anybody help me out with this question please?

---

### Post by mozetti on 2006-09-27
Try this in terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

This will re-run your X configuration for you, and you should be able to choose 1440x900 as a resolution. It's what I did when I upgraded my CRT to a wide-screen LCD.

---

### Post by Strannik on 2006-09-27
It has the same result. no changes at all. does anybody have any other ideas? I would really like to have this widescreen monitor working in linux. really strange why it works normally in freebsd and not in linux. with the same version of nvidia drivers.

---

