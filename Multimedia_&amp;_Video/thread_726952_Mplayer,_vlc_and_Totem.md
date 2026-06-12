---
title: "Mplayer, vlc and Totem"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by billgoldberg on 2008-03-17
I have three video players on my computer.

VLC, Mplayer (with gnome gui) and Totem.

VLC and Mplayer are downloaded from the medibuntu repo's, totem has restricted extras and non-free-codecs.

I mostly use vlc to view videos but every now and then I have a problem with .avi's that give me either a green bar at the top, or greenish color with the picture being mirrored a few centimeters underneath it.

example, the same .divx file played in vlc, totem and mplayer

**VLC**

[http://img26.picoodle.com/img/img26/4/3/17/f_vlcm_1befd98.png](http://www.picoodle.com/view.php?img=/4/3/17/f_vlcm_1befd98.png&srv=img26)

**Totem**

[http://img31.picoodle.com/img/img31/4/3/17/f_totemdivxm_e68a3f6.png](http://www.picoodle.com/view.php?img=/4/3/17/f_totemdivxm_e68a3f6.png&srv=img31)

**Mplayer**

[http://img33.picoodle.com/img/img33/4/3/17/f_mplayerdivxm_ceb74a6.png](http://www.picoodle.com/view.php?img=/4/3/17/f_mplayerdivxm_ceb74a6.png&srv=img33)

(sometimes vlc is the only one to play it right)

Why does this happen? And how could I fix it?

---

### Post by SonicSteve on 2008-03-17
I look forward to hearing about this. I've had this kind of problem also.

---

### Post by PmDematagoda on 2008-03-17
This thread has been moved to the Multimedia & Video section.

The pictures have also been removed as they are not allowed in posts. The links have been left intact.

---

### Post by Tomatz on 2008-03-17
Classic codec problem 

basically vlc has all codecs you will ever need onboard. Totem and mplayer require external codecs (as most are propriatory they wont be installed by default). Just have a snoop in synaptic or on the totem/mplayer website/forums for them.

---

### Post by billgoldberg on 2008-03-17
> **PmDematagoda said:**
> This thread has been moved to the Multimedia & Video section.

The pictures have also been removed as they are not allowed in posts. The links have been left intact.

I didn't know pictures weren't allowed. 

They would have helped to explain the matter better.

---

### Post by billgoldberg on 2008-03-17
> **Tomatz said:**
> Classic codec problem 

basically vlc has all codecs you will ever need onboard. Totem and mplayer require external codecs (as most are propriatory they wont be installed by default). Just have a snoop in synaptic or on the totem/mplayer website/forums for them.

VLC also has problems.

---

### Post by Tomatz on 2008-03-17
Ok lol seen pics now.

Open vlc then go:

preferences

check advanced preferences (bottom rh)

then drop down video

select output modules

and change to X11
 

Then test your video :)

---

### Post by billgoldberg on 2008-03-17
Thanks, that fixed the problems vlc had.

I wonder why this option isn't tagged by default in ubuntu.

---

### Post by Tomatz on 2008-03-17
To be honest xv (default) output should work fine i have the same problem when running compiz on my eeepc its supposed to be a bug with the intel graphics drivers.

Ps you can change the output to X11 on mplayer aswell :)

---

### Post by billgoldberg on 2008-03-17
Thanks for the mplayer tip.

I use a ati card, so it's not only the intel chipsets. And on my laptop, wich uses the intel chipset, I haven't had the problem.

---

### Post by PmDematagoda on 2008-03-17
> **billgoldberg said:**
> I didn't know pictures weren't allowed. 

They would have helped to explain the matter better.

That is why I kept the links intact, people can just click on the links to view the pictures instead of them being forced upon them, this simplifies matters at times as well:).

---

