---
title: "Media Keys not working"
date: 2014-08-09
forum: Multimedia Software
---

### Post by Jessie_James_A._At on 2014-08-09
when this was in windows 8 this media is working but replace it in  ubuntu 14.04 this media key does not work anymore except in volume &  brightness. my laptop is acer v3-571G. is it possible to make them work again? the second screenshot it shows when i press ex. fn + forward, rewind, pause, play, stop. the third screenshot show my set-up in media keys & i know it is default but why its not working, the volume keys & brightness are both working via fn + arrow*

---

### Post by TheFu on 2014-08-09
Yes, it is possible.  Just override the Fn keys inside the Window Manager. I use openbox and the config file is here: ~/.config/openbox/lxde-rc.xml

Don't know where Unity stores this. Sorry.

On 1 of my systems, I cannot override the F12 key no matter how I try. All the others work, but not that 1, probably because the HW maker decided to turn that into the power button - fracking idiots.

---

### Post by Jessie_James_A._At on 2014-08-09
ok mate, i think i dont have openbox installed.. where can i find it?

---

### Post by TheFu on 2014-08-09
Openbox is just a WM that is used by LXDE and I don't think you can use it with Unity DE.  There is a Window Manager (WM) for Unity and THAT program's settings is what you need to find. [https://en.wikipedia.org/wiki/X_window_manager](https://en.wikipedia.org/wiki/X_window_manager) can provide background.

I hope that someone else who uses Unity will respond with help.

Or perhaps the [ubuntu manual]("https://ubuntu-manual.org/") or [ubuntu guide]("http://ubuntuguide.org/") can help?

---

### Post by Jessie_James_A._At on 2014-08-09
thanks for your help mate, been trying to search in google if have time with no luck

EDIT:

PROBLEM SOLVE

---

