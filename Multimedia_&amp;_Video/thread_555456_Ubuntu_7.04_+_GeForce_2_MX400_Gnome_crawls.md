---
title: "Ubuntu 7.04 + GeForce 2 MX400: Gnome crawls"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by mikhailitsky on 2007-09-20
Hello,

I have an old box (Celeron 667, 320 MB RAM, GeForce2 MX-400) running Feisty Fawn. Recently I've managed to install video driver through System-->Administration-->Restricted Drivers Manager, which went flawlessly. The manager installed the nvidia-glx 96xx driver. Now I seem to have hardware acceleration (arrived at this conclusion after running glxgears, which was showing a decent FPS - up to 1200). However, the problem is that Gnome is still creeping slow as it was before installing the driver. I can literally see it redrawing windows and controls in them, menus are also rendered very slowly. In other words, nothing has changed in regrad to Gnome after installing the driver. So, apparently hardware acceleration is not used for Gnome. I was wondering, is there a way to employ hardware acceleration for Gnome manually/forcibly?

Thanks in advance, Denis.

---

### Post by K.Mandla on 2007-09-20
I don't know if I'm answering correctly, but I *think* the RenderAccel option might help with screen redraws and so forth. I think you can add this automatically with the nvidia-xconfig command, rather than hand-editing xorg.conf.

```
sudo nvidia-xconfig --render-accel
```
It's worth trying out. You'll have to restart X to see any effect of course, and you might even have to reboot! :shock: Horrors! :)

P.S.: By the way, isn't Gnome a bit heavy for that machine? It might be contributing to the redraw problem. ... :-k

---

### Post by ddrichardson on 2007-09-20
[nVidia]("http://www.nvidia.com") has also just released a new version of their binary driver that addresses several issues such as the black screen phenomena.

Have you checked that the correct X server is running?

---

### Post by mikhailitsky on 2007-09-20
> **K.Mandla said:**
> I don't know if I'm answering correctly, but I *think* the RenderAccel option might help with screen redraws and so forth. I think you can add this automatically with the nvidia-xconfig command, rather than hand-editing xorg.conf.

```
sudo nvidia-xconfig --render-accel
```
It's worth trying out. You'll have to restart X to see any effect of course, and you might even have to reboot! :shock: Horrors! :)

Turning this option does not quite seem to have helped :( Do you think tweaking options from the "Module" section can help at all?

Also, to me all these redraws look like as if everything was rendered directly to the screen buffer instead of being rendered to a back buffer and then instantly flipped to the screen - it very much resembles this behavior.

> **K.Mandla said:**
> P.S.: By the way, isn't Gnome a bit heavy for that machine? It might be contributing to the redraw problem. ... :-k

Well, to be honest no idea, as I'm a total newbie in Linux world (but hope to recover the situation soon :) )

---

### Post by mikhailitsky on 2007-09-20
> **ddrichardson said:**
> [nVidia]("http://www.nvidia.com") has also just released a new version of their binary driver that addresses several issues such as the black screen phenomena.

I have to stick to an older driver because the newest one does not support my video card.

> **ddrichardson said:**
> Have you checked that the correct X server is running?

Sorry, how to do that?

---

### Post by ddrichardson on 2007-09-20
It'll say which server is called in /etc/11/xorg.conf in the screen section there should be a name of a graphics card and in the device section there should be the nv driver. I just wondered because the vesa driver tends to redraw very slowly.

If not it may just require some tweaking as the MX440 series are surprisingly different between models and are not always detected correctly.

---

### Post by mikhailitsky on 2007-09-21
> **ddrichardson said:**
> It'll say which server is called in /etc/11/xorg.conf in the screen section there should be a name of a graphics card and in the device section there should be the nv driver. I just wondered because the vesa driver tends to redraw very slowly.

If not it may just require some tweaking as the MX440 series are surprisingly different between models and are not always detected correctly.

The driver name specified in that section is "nvidia"

---

### Post by ddrichardson on 2007-09-21
Well that's the right server so I guess its most likely spec related - if you open a terminal and type top, is there anything using a lot of RAM or processor time?

---

### Post by mikhailitsky on 2007-09-22
> **ddrichardson said:**
> Well that's the right server so I guess its most likely spec related - if you open a terminal and type top, is there anything using a lot of RAM or processor time?

Well, nothing unusual, most of the cycles are consumed by Xorg - 5% in average.

---

