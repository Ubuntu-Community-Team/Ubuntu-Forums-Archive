---
title: "Problems with Ubuntu and projectors"
date: 2008-12-25
forum: Multimedia Software
---

### Post by Jacob Collstrup on 2008-12-25
Heya,

I have some problems with Ubuntu 8.04 and projectors. There is a projecter at university that I know for certain can take 1024*768 pixels, however Ubuntu won't let it go higher than 800*600 this can be a problem when my laptop is used for presentations. I enter the screen resolution manager and there I can see the main screen (laptop) and a smaller secondary screen (projector), but the resolution for the projector won't go higher than 800*600, how can I set it higher?

Secondly I was trying to watch a movie over a projector that could only do 800*600, but Ubuntu figured that one fine. No problem with resolutions there. However there was no video output on the big screen. I could see the movie on the laptop screen, but the video window on the big screen was black. I could see my entire desktop on the big screen, all the icons and windows was displayed correct, except the video output. It was just black. I used the movie player that was installed with ubuntu. I've now installed VLC too, but I don't know if that'll help.

Jacob

---

### Post by linux_tech on 2008-12-25
Applications>Accessories>Terminal
what is output of ```
xrandr
```

you may try something like
```
xrandr --output VGA --mode 1024x768 --right-of LVDS

```

---

### Post by linux_tech on 2008-12-25
If there is no display on the projector screen then you may also try-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
 (with projector connected)

---

### Post by Jacob Collstrup on 2008-12-25
> **linux_tech said:**
> If there is no display on the projector screen then you may also try-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
 (with projector connected)

What do you mean with 'no display on the projector screen'?

Everything shows up on the projector screen, except the video. I can navigate my desktop on the big screen just fine. I can see the video players window. But the square that should be the video is black and empty. Making it go full-screen doesn't help. I'll give it a shot next time. It's only the streaming video itself that is missing. Its just a black box, everything else is as it should be.

Jacob

---

