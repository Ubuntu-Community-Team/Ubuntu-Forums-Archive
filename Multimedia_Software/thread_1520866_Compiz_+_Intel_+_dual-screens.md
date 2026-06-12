---
title: "Compiz + Intel + dual-screens"
date: 2010-06-30
forum: Multimedia Software
---

### Post by kaefert66014235 on 2010-06-30
Hi there!

I have got an "Intel Corporation 82945G/GZ Integrated Graphics Controller" here.

It has one DVI and one VGA port. On both these ports I have connected an Acer AL1906 with the resolution of 1280x1024.

Since they stand side-by-side and not one on top of the other I configured them to be side-by-side. This gives me a virtual resolution of 2560x1024. However, this seems to be a problem with the intel driver.

```
kaefert@ALGWS01124:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) Y

 Your resolution is 2560x1024 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 

kaefert@ALGWS01124:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
```

When I configure them in a way, that my virtual size is smaller then 2048x2048 (reducing the resolution of one of the screens and putting the one above the other virtually) then it works. 1280x2048 doesn't work (without reducing the resolution only putting one on top of the other). I think this issue has arised because some developers changed a > to a >= (see [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/561577/comments/1](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/561577/comments/1))

Does anyone have any suggestions how I can make this work? Skipping tests like that
```
SKIP_CHECKS=yes compiz --replace &
```
doesn't bring any difference.

---

### Post by kaefert66014235 on 2010-07-01
here [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/561577/comments/7](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/561577/comments/7)

somebody states that everything works alright in kubuntu, I just tried that, but for me KDE crashes as soon as I switch from the standard cloned displays to two displays side-by-side..

help?

---

