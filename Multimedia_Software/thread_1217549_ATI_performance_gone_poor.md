---
title: "ATI performance gone poor"
date: 2009-07-19
forum: Multimedia Software
---

### Post by mättu on 2009-07-19
Hi guys

Performance of my ATI-card has never been excellent, but it was o.k. on any version of ubuntu since 5.10.
Now with 9.04 (great boot times, besides) my screen is terribly slow. I speak about scrolling in pdf files or working with openoffice. (Not games or whatever).
I don't need 3D-acceleration which - to my knowledge - does not work with my card. I just need what was there all the time. No proprietary drivers etc. :-)
I fear that I am running under vesa or something by misconfiguration.
Sadly I am not even able to dpkg-reconfigure my graphics card. I mean, I can, but nothing of interest is written to xorg.conf. Seems like all settings disappeared from there. If someone could shed some light on this, please..

:m)

---

### Post by mättu on 2009-07-22
bump.

anybody?

This is a severe problem!

---

### Post by martinbaselier on 2009-07-22
It would be helpful if you told what type of card you have.
What does:
**glxinfo | grep render**
show?

if you have **top** running in a terminal window, you can see which proces is slowing down the system.

---

### Post by mättu on 2009-07-23
TCL```
glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 
```

top: there aren't any applications slowing the system down, as far as I can see. CPU is idle most of the time.

Very slow are (poor responsiveness, too): scrolling in files, switching desks, switching programms (alt - tab). It's really like if I installed Windows without graphics acceleration. :-(

I think I saw a thread about a kernel issue with Intel-cards, but I don't know if this applies generally.

---

### Post by mättu on 2009-07-27
hey friends, this issue is really severe!
I can't work on larger documents on Ooo and had to reboot into 8.04. 
I believe, many people might have this problem as well and I guess if someone has her / his first try at ubuntu with 9.04 and encounters the same problem then it will very likely be his last attempt.

I must say, I am (for the first time) a little bit annoyed with ubuntu.

Is there no help available or a patch or an update? Will this be fixed in 9.10?

Am I the only user encountering this issue? Should I ask somewhere else than in these forums?

---

### Post by martinbaselier on 2009-07-27
I'm running jaunty since december and never had this problem. No high cpu usage, driver is loaded normally so that won't be the option either. Maybe compiz is slowing stuff down? On your desktop: right mouse button, desktop settings, visual effects (I believe it's called that) and then turn off all visual effects. 

You might also consider a switch to xubuntu. In a terminal type:
sudo apt-get install xubuntu-desktop. When you login, you can then choose xfce as an aption.

---

### Post by mättu on 2009-07-28
Thank you for your valued assistance.
There is no compositor activated (just checked that again) and I've been running xubu for about 2 years at least.

My main concerns are:
- Newbies could be scared off
- Regressions get undetected

I mean what ubuntu has done over the last 5 years is absolutely fantastic. Just compare the installation today to a debian sarge installer from 2003.. But at the moment I feel that ubuntu releases too early and there are too many regressions. For me, ubuntu is easy enough to use and I would opt for rock-solid, bug-squashed releases.

I will then open a bug report over at launchpad and see what the karmic koala will be able to do with mit my graphics card. :-)

---

