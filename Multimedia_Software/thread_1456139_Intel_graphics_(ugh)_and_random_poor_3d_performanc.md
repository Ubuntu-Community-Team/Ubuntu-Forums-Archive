---
title: "Intel graphics (ugh) and random poor 3d performance - sometimes its okay sometimes no"
date: 2010-04-16
forum: Multimedia Software
---

### Post by djolk on 2010-04-16
Hi there,

I am running kubuntu 9.10 on a dell inspiron 14 with an intel GM45 graphics card. 

When I run 3d games like Nexuiz, openarena and tremulous I get really random performance. Sometimes things are totally playable with somewhere between 50-80 fps and other times I get maybe 4 fps and everything takes forever to load. These effects persists between logouts, X restarts and reboots!

I get no errors when I run things in console either.

I never really play games much but when something doesn't work...

djolk

---

### Post by kalaka on 2010-04-16
I have an Intel card too. You have to realize that integrated GPUs are rarely good (even on windows).

Your best option is to try the xorg-edgers packages for the intel drivers. These have the latest improvements and they worked well for me.

add these to System ->Administration ->Software Sources, "Other Software" tab:
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
```

then add the key and upgrade

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
sudo apt-get update
```

This made my FPS increase a little and I was able to play **some** games.

---

### Post by Native Dialect on 2010-04-16
The GM45 is an awful iGP. There is no real way to phrase that in a less blunt manner. It has low performance. I mean, sure it is a Direct3D 10 capable card, but at best, it is useful for video watching. 

If you have Compiz turned on, turn it off. It is a bit resource intensive, even if you are not actively rotating the cube or some other compiz feature. From there, you have no real options for performance improvement. I can only suggest that you avoid any Intel Graphics Media Accelerator (also known as the Intel GMA series). It is sad really. People started to get really upset over the old Intel Extreme Graphics line

[Proof that People Really do hate Intel Extreme Graphics]("http://www.google.com/#hl=en&q=Intel+Extreme+Graphics+sucks&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f")
 
Intel [S]pulled a fast one[/S] went back to the drawing board, and now you have the new GMA series. Same terrible performance, new name. Sorry sir. If you are using a desktop, then I suggest you upgrade to a new GPU. If you want something inexpensive, you can go look for an ATI Radeon HD 2600 or an nVidia GeForce 6600. They can play modern games on low settings (e.g. games like Batman Arkham Asylum and Resident Evil 5). So either of those cards would be more than enough to run Nexuiz, which is surprisingly more resource intensive than most would think.

---

### Post by kalaka on 2010-04-16
> **Native Dialect said:**
> The GM45 is an awful iGP. There is no real way to phrase that in a less blunt manner. It has low performance. I mean, sure it is a Direct3D 10 capable card, but at best, it is useful for video watching. 

If you have Compiz turned on, turn it off. It is a bit resource intensive, even if you are not actively rotating the cube or some other compiz feature. From there, you have no real options for performance improvement. I can only suggest that you avoid any Intel Graphics Media Accelerator (also known as the Intel GMA series). It is sad really. People started to get really upset over the old Intel Extreme Graphics line

[http://www.google.com/#hl=en&q=Intel+Extreme+Graphics+sucks&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f]("Proof that People Really do hate Intel Extreme Graphics")
 
Intel [S]pulled a fast one[/S] went back to the drawing board, and now you have the new GMA series. Same terrible performance, new name. Sorry sir. If you are using a desktop, then I suggest you upgrade to a new GPU. If you want something inexpensive, you can go look for an ATI Radeon HD 2600 or an nVidia GeForce 6600. They can play modern games on low settings (e.g. games like Batman Arkham Asylum and Resident Evil 5). So either of those cards would be more than enough to run Nexuiz, which is surprisingly more resource intensive than most would think.
Unfortunately, he is right. Intel GMA cards are not good on Windows, let alone Linux. If you have a desktop, change your GPU immediately, otherwise I guess you wont be able to play games on your laptop.

---

### Post by djolk on 2010-04-16
Right, Intel cards totally suck... I however bought a laptop with one in it and I am stuck with it. It barely plays DVDs! 

I guess its a good thing I only play games when I am procrastinating. However what totally baffles me and drove me to create this thread is the randomness.  Sometimes games are playable and enjoyable and sometimes they are not with no discernible reason.  In fact even rebooting the computer doesn't change anything. 

This randomness is what I am curious about. I don't really care about eeking more FPS out of this junky GPU. If it sucked all the time I would just not try and get on with it.

Anyways, ideas about the randomness?

I am going to install ArchLinux and see what more bleeding edge drivers + kernel and no KDE gain me.

---

### Post by Native Dialect on 2010-04-17
If Compiz is not running, then I am not certain. I have an ATI Radeon HD 3200 as my iGP. When I was getting performance issues, Compiz was the sole cause of them.

---

### Post by djolk on 2010-04-17
Compiz is NOT running but kwin compositing is. I shall try without. 

When 3d is going really badly KDE often disables compositing automatically but it doesn't seem to affect anything.

---

### Post by Native Dialect on 2010-04-17
Ahh. I do not use that Window Manager myself. I am not sure if it is as resource intensive as Compiz is (not that Compiz is intensive, but it can be when you start layering processes e.g. playing a video while compiz is on). Hopefully, shutting off KWin will help out some.

---

### Post by Keith1212 on 2010-04-17
I have a Mobile Intel 945GM in my laptop and I use Intel Graphics Media Accelerator Driver for Mobile. I can play wow on low settings with max 15fps and even mosey around dalaran with max 5 fps. Most of you that play wow know how hard dalaran is on a gfx card with even good ones not being able to do much there. I play Guild wars on med-high settings with 20fps. That's all I play on pc as far as needing a gfx card for.

---

