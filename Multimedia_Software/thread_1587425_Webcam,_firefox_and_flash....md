---
title: "Webcam, firefox and flash..."
date: 2010-10-03
forum: Multimedia Software
---

### Post by Klaynos on 2010-10-03
I'm trying to solve a problem for a friend of mine, he's trying to use his webcam with flash.

He's running 10.04, the cam works with ekiga, and in webcamstudio.

In gstreamer-properties we can get both the webcam and the output from webcamstudio to display fine.

But when we try and hit something like "testwebcam.com" we get flash telling us "cannot find camera" and the results of dmsg are:

> 
equested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/video3"
[ 4920.187361] type=1503 audit(1286130077.233:7884):  operation="open" pid=3585 parent=3269 profile="/usr/lib/firefox-3.6.10/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/video3"
[ 4920.195713] type=1503 audit(1286130077.241:7885):  operation="open" pid=3585 parent=3269 profile="/usr/lib/firefox-3.6.10/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/video0"
[ 4920.195733] type=1503 audit(1286130077.241:7886):  operation="open" pid=3585 parent=3269 profile="/usr/lib/firefox-3.6.10/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/video0"
[ 4920.195752] type=1503 audit(1286130077.241:7887):  operation="open" pid=3585 parent=3269 profile="/usr/lib/firefox-3.6.10/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/video1"
[ 4920.195769] type=1503 audit(1286130077.241:7888):  operation="open" pid=3585 parent=3269 profile="/usr/lib/firefox-3.6.10/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/video1"



The output from:
ls /dev/video* -l

crwxrw-rwx+ 1 root video 81, 0 2010-10-03 17:59 /dev/video0
crwxrw-rwx+ 1 root video 81, 1 2010-10-03 17:59 /dev/video1
crwxrw-rwx+ 1 root video 81, 3 2010-10-03 18:46 /dev/video3

and the output from groups includes video... 

I've tried the trick of running:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &

But that makes no noticeable difference.

Does anyone have any idea wth is going on?

Thanks

---

### Post by no2498 on 2010-10-04
did you try this for flash too

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash



if that dont help
go to the adobe site and look for the settings manager
allow the site you wish to use


hope this helps

---

### Post by Klaynos on 2010-10-04
No command 'flash' found,...

As I'd kinda expect.

The sites are set to always allow, I've tried several, they all seem to result in the same thing...

---

### Post by no2498 on 2010-10-05
im only guessing its fire fox

get and try opera

[http://www.opera.com/](http://www.opera.com/)

---

### Post by STARDOUSER on 2010-11-14
I'm having the same problem with 10.10 and a Logitech Quickcam 4000 in both Firefox and Chromium. The webcam works fine in Cheese Webcam Booth, but flash does not find any webcam: 
[http://imgur.com/emb6A.png](http://imgur.com/emb6A.png)

"ls /dev/video* -l" returns:
> crw-rw----+ 1 root video 81, 0 2010-11-14 15:44 /dev/video0

dmesg:
> [ 2545.431247] ptrace of non-child pid 1983 was attempted by: firefox-bin (pid 1982)
[ 2545.431259] ptrace of non-child pid 1984 was attempted by: firefox-bin (pid 1982)
[ 2545.431268] ptrace of non-child pid 1988 was attempted by: firefox-bin (pid 1982)
[ 2545.431277] ptrace of non-child pid 1989 was attempted by: firefox-bin (pid 1982)
[ 3157.429528] ptrace of non-child pid 2115 was attempted by: firefox-bin (pid 1982)
[ 3157.429540] ptrace of non-child pid 2116 was attempted by: firefox-bin (pid 1982)
[ 3157.429549] ptrace of non-child pid 2120 was attempted by: firefox-bin (pid 1982)
[ 3157.429558] ptrace of non-child pid 2121 was attempted by: firefox-bin (pid 1982)
[ 3159.412490] lo: Disabled Privacy Extensions
[ 3321.072851] ptrace of non-child pid 2277 was attempted by: firefox-bin (pid 1982)
[ 3321.072863] ptrace of non-child pid 2278 was attempted by: firefox-bin (pid 1982)
[ 3321.072872] ptrace of non-child pid 2282 was attempted by: firefox-bin (pid 1982)
[ 3321.072881] ptrace of non-child pid 2283 was attempted by: firefox-bin (pid 1982)

video4linux shows:
> 
version 10.0.12
capabilities: 0x05000001

---

### Post by no2498 on 2010-11-15
as i said in my last post get opera

---

### Post by STARDOUSER on 2010-11-16
> **no2498 said:**
> as i said in my last post get opera

Thanks, but it doesn't work in Opera either. 
Opera version 10.63
Flash version 10.1.102.64
10.10 Ubuntu 32-bit

Going to try installing x64 Ubuntu so I can try that version of flashplayer

---

### Post by no2498 on 2010-11-16
odd i use it in both computers 1 with 804 on it and 1 with 10.04 on it 32 bit's
both use flash for my webcams

---

### Post by STARDOUSER on 2010-11-16
Same story on 64-bit Ubuntu with the new x64 preview build of Flashplayer "square" (version 10.2.161.23). Flashplayer shows the "Cannot find camera" message. The webcam is confirmed working with Cheese Webcam Booth.

This doesn't yield any differences either:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so opera

---

