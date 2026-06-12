---
title: "32bit libGL.so not functioning on 64bit Natty"
date: 2011-07-26
forum: Multimedia Software
---

### Post by james.christie on 2011-07-26
I am running a Dell Vostro laptop with Intel Sandy Bridge HD3000 graphics. In an attempt to fix the issues with it I added the xorg-edgers PPA to my sources list and installed the updates. Performance is now fantastic and all the bugs dissapeared except for one issue. Hardware acceleration for 32bit applications is not available. Applications complain of a missing libGL.so.1 file which is strange considering I can find it here:

```
james@medium-conqueror:~/Games$ ls -alF /usr/lib32/libGL*
lrwxrwxrwx 1 root root     15 2011-05-31 10:05 /usr/lib32/libGL.so -> mesa/libGL.so.1
lrwxrwxrwx 1 root root     11 2011-05-31 10:05 /usr/lib32/libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2011-05-31 10:05 /usr/lib32/libGLU.so.1 -> libGLU.so.1.3.071000
-rw-r--r-- 1 root root 439976 2011-04-19 05:54 /usr/lib32/libGLU.so.1.3.071000
```

The biggest gripe about this is that I am unable to run any applications via Wine requiring hardware acceleration, however any 64bit applications work very happily.

---

### Post by José Luis Bolos on 2011-07-29
I share your pain.

I noticed that in my system there was no libGL* symbolic link in /usr/lib so I did a:
```
ln -s /usr/lib32/mesa/libGL.so.1 /usr/lib/libGL.so.1
```
and it's working again, although I don't understand why the link isn't there (should be created automatically by the update-alternatives thingy) or if it's a good idea to create it at all (probably don't). :confused:

---

