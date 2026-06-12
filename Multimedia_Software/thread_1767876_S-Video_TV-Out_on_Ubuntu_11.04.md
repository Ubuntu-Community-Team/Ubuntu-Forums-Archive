---
title: "S-Video TV-Out on Ubuntu 11.04"
date: 2011-05-26
forum: Multimedia Software
---

### Post by crabshank on 2011-05-26
I was just wondering if it was possible to use s-video tv-out with an Nvidia GeForce2 MX/MX400 graphics card on Ubuntu 11.04.

---

### Post by novinick on 2011-05-26
you need proprietery nvidia legacy driver.

 I think 96.xx supports geforce 2 mx
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

 I think 96.xx should work on new xorgs, not sure

 It is in repos
 [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
 [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

> for 10.10 , Version 96.43.18 is broken ,Go to **System->Administration->Software sources** then go to the update's tab--tick proposed update sources--close & refesh.  This link has more informationyes he's in repos
**(96.43.19-0ubuntu8)**

[http://packages.ubuntu.com/natty/nvidia-glx-96](http://packages.ubuntu.com/natty/nvidia-glx-96)

you'll get menu item in gnome-menu, called "nvidia setting" where to setup tv out

---

### Post by novinick on 2011-05-26
well, perhaps not on natty :(
[http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html)
 > Added  support for X.Org xserver 1.9.
Added  support for X.Org xserver 1.8.
Updated  nvidia-installer to detect the nouveau kernel module and fail with an  appropriate error message.
11.04
natty has xorg server 1.10.1
and 
10.10
maverick has xorg server      1.9.0
so it is safe to say it will work on merkaat ;)

:popcorn:

---

