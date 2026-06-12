---
title: "Natty problems, maybe with my Intel Corporation Mobile 915GM Graphics card"
date: 2011-04-30
forum: Multimedia Software
---

### Post by trombipeti on 2011-04-30
Hi,
I've installed like two weeks ago a kubuntu 11.04 beta 2. Then I installed ubuntu-desktop so that I have unity and gnome running now. I upgraded every day, so now I have Ubuntu 11.04.
My problem is that either I use Unity, Gnome or KDE, my screen sometimes "randomly" freezes, and I can only go to tty1 and restart my computer. Although, sometimes by perssing Ctrl+Alt+F1 nothing will happen, so I have to push my laptop's power button for 5 secs to switch it off.
Sometimes even the login screen freezes (when I click on my name to sign in), I can't type in my password, and nothing appears on the bottom panel. The only solution is pressing the power button.
First, I thought it was the problem of compiz, because I got a message when I tried to login with Unity which was like "you don't have good enough machine to run Unity, please use classic ubuntu desktop - which is gnome. But after KDE and even the login screen froze, I think it's some kind of problem with my graphics card. Here are it's details:
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00[VGA controller])
Subsystem: IBM device 0582
I have the driver installed afaik. Maverick run well, I had lots of compiz effects (cube etc) enabled and it had no problem. But now, on Natty, it sometimes works, but sometimes it doesn't. Same with Kwin effects.
I have no clue what to do. I'm so sad because now I have to use Windows, because my Ubuntu is very unstable.

Peter

---

### Post by Toufik on 2011-05-01
I double you!

Same here with a laptop with a Intel 915GM

$ lspci
...
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
...

I'd be happy to fix that. I really like the new interface but it's so unstable!! I've even got some random X11 restarts! Like every 30min-1h...

---

### Post by jclw on 2011-05-04
As a workaround, it's working fine for me with the old 2.6.36 vanilla kernel from kernel-ppa.

---

### Post by trombipeti on 2011-05-05
I've got some nice kernel panic for the first time trying to boot with 2.6.36...... I might've messed up sg.
Should I just simply download the .deb files and dpkg -i them, or do I have to compile the kernel myself? (I believe the I don't since the kernel ppa has .deb files)
Thank for your help though.

---

### Post by jclw on 2011-05-06
> **trombipeti said:**
> I've got some nice kernel panic for the first time trying to boot with 2.6.36...... I might've messed up sg.
Should I just simply download the .deb files and dpkg -i them, or do I have to compile the kernel myself? (I believe the I don't since the kernel ppa has .deb files)


Hm, that's what I did.  

However, there's something else you can try: Since yesterday, I have been using the updated drivers from the [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa without any problems (together with the stock 2.6.38-8 kernel):  
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by trombipeti on 2011-05-06
Thanx, I've installed the new drivers, hope it will work.
Offr topic: why did you write aptitude in the commands? is this something you personally use, or should my system also use that? (Now it uses apt-get)

---

### Post by jclw on 2011-05-07
> **trombipeti said:**
> 
Offr topic: why did you write aptitude in the commands? is this something you personally use, or should my system also use that? (Now it uses apt-get)
Hm, that's just what I use; for most stuff it really doesn't make a difference however, and the preferred tool on Ubuntu is indeed apt-get (and Debian prefer aptitude, last time I checked).

---

