---
title: "fglrx and freezes"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by Sneseglarn on 2005-11-08
I followed the Howto and installed ATI's binary fglrx driver ( 8.18 ) everything else (except cedega) comes from the apt-repositories.. 

Now here is the problem:
Xscreensaver (not all of them, but 99% av the gl-screensavers and many others) Cedega, and GL-apps in general causes hard freeze on my system.. it works fine for a few minutes, and then it all dies.. no capslock on/off , no nothing so i have to yank the power..

My system is:
Ati athlon xp 3200, 1gig ram (memtested), asus a7n8x (nforce2) , Ati Radeon 9600xt

the gl-screensavers work (but at 1fps obviously) with software only, but once i get dri, the system becomes quite unstable..

anybody have a clue? , (or do you need some confs & logs?)

Kind Regards / Mark

---

### Post by brj on 2005-11-12
[QUOTE=Sneseglarn]I followed the Howto and installed ATI's binary fglrx driver ( 8.18 ) everything else (except cedega) comes from the apt-repositories.. 

Now here is the problem:
Xscreensaver (not all of them, but 99% av the gl-screensavers and many others) Cedega, and GL-apps in general causes hard freeze on my system.. it works fine for a few minutes, and then it all dies.. no capslock on/off , no nothing so i have to yank the power..

My system is:
Ati athlon xp 3200, 1gig ram (memtested), asus a7n8x (nforce2) , Ati Radeon 9600xt

the gl-screensavers work (but at 1fps obviously) with software only, but once i get dri, the system becomes quite unstable..

anybody have a clue? , (or do you need some confs & logs?)

Kind Regards / Mark[/QUOTE]

hi mark,

my system freezes as soon as i start x

see: [http://www.ubuntuforums.org/showthread.php?p=485835](http://www.ubuntuforums.org/showthread.php?p=485835)

jakob

---

### Post by mlomker on 2005-11-12
The usual troubleshooting is to look at /var/log/Xorg.0.log and the output of **dmesg | grep fglrx** (or scroll through the whole /var/log/kern.log file).

Beyond that I suppose you'd have to find a way to debug the specific applications.  They just released the 8.19.10 driver but I'm not sure if it'd help...biggest change was suspend/resume on laptops.

---

