---
title: "Compiling xawtv4"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by Rever75 on 2006-11-12
Hi,
   I am trying to compile xawtv4 under Edgy Eft. I need to use 4 since I am using an mpeg2 tv encoder. I have installed all the development libraries (at least I think I did). I have done ./configure and it fails at make. Here is the error
```
x11/v4lctl.c:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
x11/v4lctl.c: In function ‘main’:
x11/v4lctl.c:99: error: ‘dpy’ undeclared (first use in this function)
x11/v4lctl.c:99: error: (Each undeclared identifier is reported only once
x11/v4lctl.c:99: error: for each function it appears in.)
x11/v4lctl.c:99: warning: implicit declaration of function ‘XOpenDisplay’
x11/v4lctl.c:101: warning: implicit declaration of function ‘init_atoms’
x11/v4lctl.c:110: warning: implicit declaration of function ‘XCloseDisplay’
make: *** [x11/v4lctl.o] Error 1
```

Any help would be greatly appreciated. Also if anyone knows of a Ubuntu Repo or package please let me know. I plan on using checkinstall to install so I can uninstall using dpkg -r. Again any help would be great. 



Ok issue was did not have xorg-dev and the Athena Widgets X libraries. 

Rich

---

