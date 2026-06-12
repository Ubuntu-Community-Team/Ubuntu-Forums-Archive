---
title: "webcam sn9c202 (sonix) working perfectly in U10.10 but not U11.04"
date: 2011-07-19
forum: Multimedia Software
---

### Post by bgrau2000 on 2011-07-19
practically out of the box in U10.10, well modulo a little tweak to force /dev/video0 as the default webcam... (as I have a PCI capture card)...

Both upgrade from 10.10 or fresh install of 11.04, 
in 11.04 sn9c202 fails to work on most webcam apps, apart from xawtv... weird but true...

anyone fixed this issue, or have pointers?
appreciated... as this stops me from upgrading to 11.04... (I use my webcam a lot for msg'ing)

Cheers

Billy G

---

### Post by no2498 on 2011-07-20
in a terminal type dmesg click enter
in your package manager look for and install xawtv
try the cam in xawtv first

---

### Post by bgrau2000 on 2011-07-20
> **no2498 said:**
> in a terminal type dmesg click enter
in your package manager look for and install xawtv
try the cam in xawtv first

That means I will need to re-update to 11.04...

anyways, it works perfectly on 10.10...

I tried dmesg on 10.10 just for fun, it is nice :-)

on xawtv in 11.04, it worked already as I said... it is with the other apps that there was a problem...

thanks for your suggestion, i will try it when i muster the courage (and find the time) to re-update to 11.04... :)

---

### Post by no2498 on 2011-07-21
look in applications Internet ekiga soft phone
try the cam in it

---

### Post by no2498 on 2011-07-21
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

you try that yet

---

### Post by bgrau2000 on 2011-07-21
> **no2498 said:**
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

you try that yet


Thanks dude...

just to let you know, I answered myself here:

[https://answers.launchpad.net/ubuntu/+question/165379](https://answers.launchpad.net/ubuntu/+question/165379)

---

### Post by bgrau2000 on 2011-08-28
Every new update brings its woes, and it is boring :(

Ubuntu 11.04 updated video4linux, and the libraries are no longer in the usual path which was:
/usr/lib/libv4l/
to:
/usr/lib/i386-linux-gnu/

the library names have changed too, so that what was (e.g.)
/usr/lib/libv4l/v4l2convert.so

has become:
/usr/lib/i386-linux-gnu/libv4lconvert.so

anyways, I have not found out where v4l1compat.so or its new name is, so cannot use this:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

there is a file called:
/usr/lib/i386-linux-gnu/libv4l1.so

and I wonder if changing to 
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l1.so skype

will yield a viewable video...

I find it very annoying when developers do this and do not advise how to take account 
of the changes, sloppy programming...

If anyone has a clue, will appreciate the share :(

add:
I tried LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l1.so skype and it does not work... :(

---

### Post by bgrau2000 on 2011-08-29
Well I fixed it for myself...

the workaround is to get a copy of the missing folder that contains the old v4l libraries and put it where it used to be... (I was lucky to have a non-upgraded virtualbox with ubuntu 11.04), so the path for the libraries needed was:
 /usr/lib/libv4l/ 
with the crucial file
v4l1compat.so

that being said, the developer/s needed to let us know that they deprecated the compatibility for v4l1... and offer an alternative, or at least offer this workaround...

I am attaching the folder if anyone needs it, and it must be put in /usr/lib/

:)

---

