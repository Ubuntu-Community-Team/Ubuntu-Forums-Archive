---
title: "Karmic Intel 865 Graphics issues"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Julian David Pitt on 2009-12-19
I am using an old Dell GX270 desktop and am having issues with the video output. When Karmic was installed I could only achieve 1152 x 864 (4:3) which leaves me with a blank area at the top and bottom of my 18" screen. In an effort to get 1280 x 1024 I added the repository for the Ubuntu X drivers and installed a newer version. This made no difference to the resolutions available to me. I have resorted to using 1024 x 768 in order to better fill the screen. When I run lspci I get the following output:
```
Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)

```
 If I try to view my Xorg.conf file it opens in a blank window for some reason? If I browse to /etc/x11 I cannot see an Xorg.conf file. Can someone tell me how I can further fault find this please.

---

### Post by Julian David Pitt on 2009-12-27
Bump

A week now with no reply, what am I doing wrong?

---

### Post by Kasm279 on 2010-04-16
Well, it seems as though the i865 chipset isn't supported properly, but i can get 1680x1050 on mine, just no hardware acceleration. Try going to Ubuntu 8.10, they broke it in 9.04 :confused:

---

