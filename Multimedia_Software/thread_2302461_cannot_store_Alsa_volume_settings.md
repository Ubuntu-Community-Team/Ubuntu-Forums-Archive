---
title: "cannot store Alsa volume settings"
date: 2015-11-10
forum: Multimedia Software
---

### Post by Dedalus1983 on 2015-11-10
Hello, I am using Ubuntu-Gnome 15.04 on a Dell laptop.
So I am using Jack, Pulseaudio (bridged), Alsa. Lowlatency kernel.

I have this problem: the low-level volume configuration (alsamixer) are always badly setted.
It works like someone (guessing pulseaudio) is changing it:
- when I reboot the system
- when I plug in the jack cable to connect an external speaker
- when I plug out the jack cable

It seems to me perfectly right to change the volume when these events happen.
But I would like to set myself the level (and most annoying, some channel are muted when I do no want them to be so).

If I type alsactl store then I can do restore and everything's fine, but when I reboot or plug in/out the cable all goes wrong again..

Any help? Has it something to do with /usr/share/pulseaudio/alsa-mixer/paths/* ??

Thanks

---

