---
title: "No Video SKYPE"
date: 2010-04-12
forum: Multimedia Software
---

### Post by mju4t on 2010-04-12
Hello,

I've tried many things to get Skype to recognize my webcam but Skype is being rather stubborn.  My webcam does work - I can use it in CHEESE and I can use it in Chatroulette.  Skype does see my webcam but when I click "test video" the test box just stays black and in the terminal, this message is displayed:

X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 

Can anybody help me decipher this code?  What is going on?  I've tried starting Skype with 

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

and I still get the error.

Any help?
Cheers!
Alex

oh, ps, running 64 bit karmic on a Sony Vaio VGN-NW240F

---

### Post by gradinaruvasile on 2010-04-12
See here:

[http://forum.skype.com/topic/411441-skype-21-video-feedback/page__st__60__p__2101631&#entry2101631__s__6a18e1e9c46c5cb5956eb40f84594033](http://forum.skype.com/topic/411441-skype-21-video-feedback/page__st__60__p__2101631&#entry2101631__s__6a18e1e9c46c5cb5956eb40f84594033)

Maybe it will work for you...

---

### Post by mju4t on 2010-04-12
WOW!

Running this script did it!

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
skype


THANK YOU SO MUCH!!!

---

