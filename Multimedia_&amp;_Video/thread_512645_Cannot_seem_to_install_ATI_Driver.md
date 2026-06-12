---
title: "Cannot seem to install ATI Driver"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by Jim_C on 2007-07-29
I have tried just about everything I could find but after following the wiki instructions both method 1 and 2 to install, I still get this reported from 

[INDENT]$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)[/INDENT]

Please, ANY ideas on what I can do to get the driver installed correctly? As far as the 2D stuff, it seems to be working correctly, I have ATI Control Center and I am able to switch screen resolutions and refresh rates, so that seemed to install correctly, but I cannot seem to get the open gl installed correctly....I'm about to give up on Ubuntu if I can't get this to work....

Thanks,
Jim

---

### Post by linuxwizard on 2007-07-30
Have you searched the forum for ATI your model # 


[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Jim_C on 2007-07-31
I was able to get everything working using the ATI drivers but I had to blacklist some modules because of a bug supposedly. I simply installed the latest ATI drivers and the followed this workaround 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684/comments/37](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684/comments/37)

After blacklisting those modules, the fglrxinfo command returned the correct info...and now I have Beryl working on my machine :-)

---

