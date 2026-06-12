---
title: "Skype video capturing green noise"
date: 2015-04-30
forum: Multimedia Software
---

### Post by Yordan_Yordanov on 2015-04-30
Hi

Recently I've put 64-bit Ubuntu 15.04 on my Dell Inspiron 15 5548. I am experiencing big troubles with the video in Skype. It is capturing with big green static noise, while with other programs such as Cheese, the camera works just fine. 

I've been trying to solve this for a few days now, but nothing seems to work. 

I've tried preloading the video4linux libraries, both the 32 and 64 versions with no luck
With 
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```
I get "libv4l2: error dequeuing buf: Invalid argument" when I close the test video window.

and with the 64bit version I get the following error on startup.
```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so skypeERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.



```

Also I've tried to adjust the settings with v4l2ucp and guvcview again with no luck. Some adjustments do take effect but the green static remains. 

Any help will be much appreciated!
Cheers
Dan

---

