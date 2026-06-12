---
title: "Dvd ripping"
date: 2013-01-11
forum: Multimedia Software
---

### Post by aronwalker on 2013-01-11
Does anyone know any tools to rip a dvd to be stored on my desktop. I don't worry about size. I would like it to be in one file but with all the subtitles and extra features. I tried ripping it to an iso but this only made the title screen show, and then vlc crashed. Is this legal (its only going to be used by Me + family), is they a format that can store a dvd in a file, and is they a tool that allowes me to do this? Also it needs to work on encripted dvd's (I've got the libs)

Aaron

---

### Post by oldos2er on 2013-01-11
I use k3b to rip DVDs to an *.iso file.

---

### Post by zenkaon on 2013-01-11
Handbrake is what you want, about 1 ~ 1.8 GB per DVD depending on how complex the film is:
[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by eenofonn on 2013-01-12
I'd second the motion for Handbrake but as far as collecting EVERYTHING you could always use "dd" to clone the disc to .iso

---

### Post by aronwalker on 2013-01-12
K3b - I'm using gnome

Hand break - this is the sort of tool I am looking for, but does it enable copying of encripted dvd's. On the website it says it can't do copy protected - is this the same as encripted (don't know a lot about dvds)

Dd - use this already for small scale server stuff so this may be useful - don't know if they is a gui front end for it yet - may be hard for the rest of the family to use (if they ever do)

Aaron

---

### Post by JohnAStebbins on 2013-01-12
> **aronwalker said:**
> Hand break - this is the sort of tool I am looking for, but does it enable copying of encripted dvd's. On the website it says it can't do copy protected - is this the same as encripted (don't know a lot about dvds)

The package that HandBrake distributes doesn't include everything you need to decrypt DVDs.  But it will use libdvdcss dynamic library if it is installed on the system.  HandBrake doesn't claim support for this because installing this library can be problematic on windows and osx and they don't want to be in the business of customer support for libdvdcss installation questions.

---

### Post by Rob Sayer on 2013-01-12
Personally, if it's a newer dvd/encryption scheme I'd probably run dvdfab hd decrypter in wine or virtualbox.  They're pretty good at keeping up with new standards (the bane of open source environments), and it's the free part.

---

### Post by leclerc65 on 2013-01-12
> **aronwalker said:**
> K3b - I'm using gnome

It doesn't matter - you just get ton of extra packages.
I don't like KDE but I can't live without k3b, kTorrent.

---

### Post by Rob Sayer on 2013-01-13
> **leclerc65 said:**
> It doesn't matter - you just get ton of extra packages.
I don't like KDE but I can't live without k3b, kTorrent.

Don't use KDE myself either ... I like xfce ... but I won't use any other file manager than dolphin.

---

