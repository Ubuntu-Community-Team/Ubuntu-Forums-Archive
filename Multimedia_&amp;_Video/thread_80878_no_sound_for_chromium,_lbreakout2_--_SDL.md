---
title: "no sound for chromium, lbreakout2 -- SDL??"
date: 2005-10-23
forum: Multimedia &amp; Video
---

### Post by JasonDennis on 2005-10-23
I have sound from my sb awe64 isa card after adding appropriate modules to 
/etc/modules :

[INDENT]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
snd-sbawe
snd-pcm-oss
snd-mixer-oss
snd-seq-oss
lp
mousedev
psmouse
nvidia[/INDENT]

it now appears I have no sound for games like chromium or lbreakout2, I believe these games use the SDL libraries for sound, but am not sure. 
Are there more modules that I should be loading??
Any help would be much appreciated.
Thx.

---

### Post by JasonDennis on 2005-10-24
Update:

I have observed that the sound for these games now works about 75% of the time, after changing esd.conf to this:

> 
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-terminate -nobeeps -as 2


 so I guess sometimes when I start the game the sound server must be busy... not sure how to fix.

---

### Post by budda on 2008-03-07
the second tip solved the problem for me: [http://ubuntuforums.org/showpost.php?p=3152472&postcount=8](http://ubuntuforums.org/showpost.php?p=3152472&postcount=8)

---

### Post by owise1 on 2008-04-26
Can either of you post the error message when you start the game from a console?

I get:

SNDCTL_DSP_SETFRAGMENT: Invalid argument
Warning: Couldn't set audio fragment size
Audio write: Invalid argument


Dave

---

