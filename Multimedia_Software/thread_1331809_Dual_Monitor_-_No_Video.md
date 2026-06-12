---
title: "Dual Monitor - No Video"
date: 2009-11-19
forum: Multimedia Software
---

### Post by btermeli on 2009-11-19
Hey all,

I have 9.10,dual monitor system with Intel 915 graphic card.

My problem is;  during skype call or in video player (vlc, movieplayer etc.) I cannot see anything but black screen.

No aminations, compiz is disabled.

Any idea to see the videos?

---

### Post by exploitations on 2009-11-19
Do you have your graphics drivers enabled?

---

### Post by btermeli on 2009-11-20
Sure :)

```
lspci | grep VGA
```
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

```

```
 glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2

```

---

### Post by erop on 2009-12-07
Exactly the same problem on Karmic :(

```
erop@u5f:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```
```
erop@u5f:~$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2

```

Any ideas how to fix that?

---

### Post by erop on 2009-12-07
Thanks to btermeli now we have a decision for VLC only. You should set up Output value to "X11 Output" in Tools -> Preferences -> Video.

---

### Post by btermeli on 2009-12-08
Hey again,

I solved the problem for other video players but not skype yet.

Alt +F2

```
gstreamer-properties
```

Then Video tab > Output and choose

X Windows System (No Xv)

Restart and give a try to video player.

---

