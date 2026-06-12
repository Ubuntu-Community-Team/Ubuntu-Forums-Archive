---
title: "Problem with X using nvidia drivers on Dapper Drake 6.06 LTS"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by wheezart on 2006-07-30
I have a Nvidia Ge-Force MX 440 and I'm having problems starting X after enabling the drivers. I'm using Kubuntu btw =)
I've tried:
1. To manually edit xorg.conf - replaced "nv" with "nvidia" in "Device"
2. Use the "enable" script included in the drivers
3. To place   load "glx" before load "GLcore"

Whatever I do, X fails to start after the load screen and stalls with an empty progress bar untill i press Ctrl-Alt-Del and reboot.
When booting into recovery mode, startx displays this:

```
LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastCont
ext
```

Can someone lend a hand, It's really making me :(

---

### Post by tseliot on 2006-07-30
1) First of all get the Xserver to work again:

boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

2) Then install the Nvidia driver:
Read this guide of mine:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

and have a look at point 7 of the Problems Section of that guide.

---

### Post by wheezart on 2006-07-30
Thanks for the timely response, i'll try that right away =)

---

