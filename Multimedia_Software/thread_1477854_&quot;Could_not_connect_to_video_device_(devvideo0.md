---
title: "&quot;Could not connect to video device (/dev/video0), please check connection&quot; error"
date: 2010-05-09
forum: Multimedia Software
---

### Post by hihihi100 on 2010-05-09
The title of the thread is what I get when I turn on Camorama. I have done a quick search in the forums and found:

[http://newyork.ubuntuforums.org/showthread.php?t=1299976](http://newyork.ubuntuforums.org/showthread.php?t=1299976)

So Im executing those same commands, to try to know the reason of the error message:

In another post (I cant recall which one) I found a post that said that if that message appears (Could not connect...), that means that the OS recognizes that there is an installed webcam (in my case is an eyeshot one that comes pre installed with the laptop). Please confirm if this is true or not.

for lsusb:

```
lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Realtek semi... doesnt look like a webcam to me, please correct me if wrong

For -la /dev/video0:

```
ls -la /dev/video0
ls: cannot access /dev/video0: No such file or directory
```

However, if I type ls -la /dev/v*:

```
ls -la /dev/v*
crw-rw---- 1 root tty   7,   0 2010-05-09 05:32 /dev/vcs
crw-rw---- 1 root tty   7,   1 2010-05-09 05:32 /dev/vcs1
crw-rw---- 1 root tty   7,   2 2010-05-09 05:32 /dev/vcs2
crw-rw---- 1 root tty   7,   3 2010-05-09 05:32 /dev/vcs3
crw-rw---- 1 root tty   7,   4 2010-05-09 05:32 /dev/vcs4
crw-rw---- 1 root tty   7,   5 2010-05-09 05:32 /dev/vcs5
crw-rw---- 1 root tty   7,   6 2010-05-09 05:32 /dev/vcs6
crw-rw---- 1 root tty   7,   7 2010-05-09 05:32 /dev/vcs7
crw-rw---- 1 root tty   7, 128 2010-05-09 05:32 /dev/vcsa
crw-rw---- 1 root tty   7, 129 2010-05-09 05:32 /dev/vcsa1
crw-rw---- 1 root tty   7, 130 2010-05-09 05:32 /dev/vcsa2
crw-rw---- 1 root tty   7, 131 2010-05-09 05:32 /dev/vcsa3
crw-rw---- 1 root tty   7, 132 2010-05-09 05:32 /dev/vcsa4
crw-rw---- 1 root tty   7, 133 2010-05-09 05:32 /dev/vcsa5
crw-rw---- 1 root tty   7, 134 2010-05-09 05:32 /dev/vcsa6
crw-rw---- 1 root tty   7, 135 2010-05-09 05:32 /dev/vcsa7
crw-rw---- 1 root root 10,  63 2010-05-09 05:32 /dev/vga_arbiter

```

And for camorama -D:

```
camorama -D
VIDIOCGCAP  --  could not get camera capabilities, exiting.....

```

It seems that Ubuntu 10.04 doesn't recognize the embedded webcam of my laptop. Now, if any of you has any other command that I should run, please share.

Cheers

---

### Post by no2498 on 2010-05-09
see if this helps

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

try the cam in cheese

hope this helps

---

### Post by phorminx on 2010-05-24
I was having similar difficulties when trying to use camorama. In the end, I realized that this is really a problem of camorama only. My webcam works fine with gstreamer-properties and cheese.

---

### Post by afrodeity on 2010-09-05
> **phorminx said:**
> I was having similar difficulties when trying to use camorama. In the end, I realized that this is really a problem of camorama only. My webcam works fine with gstreamer-properties and cheese.

me too, seems like development stopped in 2006. Somebody needs to take this app over, it is way too old. Can't believe we hardly have any choice when it comes to webcams in Ubuntu, just cheese (which always breaks) and wxCam which is a bit futzy. Time to get a sponsor an app programme going becaus e we like a distro where the only cool apps are sound apps. Every other app except gimp, sucks.

---

### Post by afrodeity on 2010-09-05
[http://ubuntuforums.org/showthread.php?t=1299976](http://ubuntuforums.org/showthread.php?t=1299976)

---

### Post by no2498 on 2010-09-05
wxcam has worked well for me

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

