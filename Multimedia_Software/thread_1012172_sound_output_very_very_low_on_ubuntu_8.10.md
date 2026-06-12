---
title: "sound output very very low on ubuntu 8.10"
date: 2008-12-15
forum: Multimedia Software
---

### Post by TMachado on 2008-12-15
I've installed ubuntu 8.10 on Toshiba A210-AC, but sound output is very low, it's very difficult to hear. 

What's the problem?

---

### Post by rybl on 2008-12-15
Maybe try ```
sudo alsamixer
``` in the terminal and play with your levels some.

---

### Post by TMachado on 2008-12-15
> **rybl said:**
> Maybe try ```
sudo alsamixer
``` in the terminal and play with your levels some.

No.. it's already in maximum...

[IMG]http://img76.imageshack.us/img76/5148/capturaecra1ei5.png[/IMG]

And I've noticed another problem. Both my "system sounds" are playing same time! :confused:

---

### Post by rybl on 2008-12-16
I came across another posting ([http://ubuntuforums.org/showthread.php?t=373287](http://ubuntuforums.org/showthread.php?t=373287)) that was having a similar problem

they were able to fix it by adding ```
options snd-hda-intel model=3stack
``` to /etc/modprobe.d/alsa-base

---

### Post by TMachado on 2008-12-16
> **rybl said:**
> I came across another posting ([http://ubuntuforums.org/showthread.php?t=373287](http://ubuntuforums.org/showthread.php?t=373287)) that was having a similar problem

they were able to fix it by adding ```
options snd-hda-intel model=3stack
``` to /etc/modprobe.d/alsa-base

That line is already there...

---

### Post by rybl on 2008-12-16
Hmm, sorry I can't think of anything else, but if I come across anything I'll post it here.

---

### Post by TMachado on 2008-12-16
> **TMachado said:**
> No.. it's already in maximum...

[IMG]http://img76.imageshack.us/img76/5148/capturaecra1ei5.png[/IMG]

And I've noticed another problem. Both my "system sounds" are playing same time! :confused:

In that image,  'headphone' is the output for headphones, and 'front' is the output of my pc. If I put 100 in both I have sound on both sides, so I want to have on just one, I have to do it mannualy...

---

