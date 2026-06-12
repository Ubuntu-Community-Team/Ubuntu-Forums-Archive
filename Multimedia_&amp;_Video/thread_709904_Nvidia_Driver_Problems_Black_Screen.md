---
title: "Nvidia Driver Problems: Black Screen"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by InuIzzy on 2008-02-27
Goal: Get 3D graphics to work so I can play Enemy Territory or ANY 3D game.

I have looked all over the forums and have tried for many hours to get my Nvidia driver to work properly

So now after all my work I have gotten  to where I have "Nvida Setiing" in my System tools this is after using Envy in hopes that it would fix the problem but no such luck. I have the Nvidia Restricted Driver disabled because it causes my screen to be black after boot when I should be looking at my login screen. I think its Xserver and when ever this happens I type 

```

sudo fixit

```

But sadly I cant tell you what it does other than my friend set it up and it turns of the Nvidia Restricted Driver. When I open Nvidia Settings this is the message I get.

*You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. *

When I run `nvidia-xconfig` I get the same black screen problem. The *fixit* command my friend set up seems to turn this off also. I am very frustrated but I am not giving up. Can some one please give me some advise on how to fix this.

Possibly useful Info:
Running 7.10
Graphics Card: Nvidia GeForce FX 5200
Ask if you need anything else.

---

### Post by A4006 on 2008-02-27
I have had this problem not once but twice, second time was just because I'm stupid... Anyways, to be honest I just messed around with the drivers until it worked (BTW, I have a XFX GeForce 8500 GT), although it seems like I used Envy to uninstall the drivers completely, and then reinstalled with Envy after disabling the proprietary drivers, if that makes any sense. Hope this helps.

---

### Post by InuIzzy on 2008-02-27
I tried that except I didn't disable the proprietary drivers, can you (or some one) tell me what you mean by that.
By the way, I am new to Ubuntu but I have pick up a little bit on who to do things.

---

### Post by muddyz on 2008-02-28
Not sure if it's the case with that card and drivers but with my 8800 i had to set the boot to nosplash or else i got a black screen on startup.

---

