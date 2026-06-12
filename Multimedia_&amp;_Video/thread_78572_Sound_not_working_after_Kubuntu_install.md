---
title: "Sound not working after Kubuntu install"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by Wmknox on 2005-10-18
I just recently upgraded to 5.10, which removed the kubuntu-desktop packages from my machine, and after the upgrade, aside from some slight trouble with nVidia drivers and ndiswrapper, everything was working perfectly. I wanted KDE back (I flop between Gnome and KDE every so often), so I installed kubuntu-desktop through apt-get. The installation went fine, except now I can no longer get sound from Gnome or KDE. If I have to remove KDE in order to fix this, I don't mind, but I would really like to get sound back.

---

### Post by Wmknox on 2005-10-19
Okay, I managed to remove KDE without a problem, but my sound still doesn't work. Is there any way to return ALSA, OSS, and ESD to their setup before the installation?

---

### Post by thomax on 2005-10-19
I have the same problem. But my home dir is at a different partition so I could keep the user data. During the install you have to make one user, the administrater, I gave it the same name as before, etc. In that acc I still have sound but in the others, which I've added later (but still have data from 5.04) the sound is lost :(

Could not open /dev/dsp useing the null output

---

### Post by Seahawk on 2006-02-23
just went through the same thing 
had sound Alsa working fine under ubuntu Breezy with gnome,  audigy 4 sound card 
I decided to try out KDE desktop
after the KDE install sound will not work
tried reinstalling alsa 
tried switching back to Gnome desktop 
no sound there either
any ideas?????

new to linux appreciate any help out there
SeaHawk

---

### Post by Seahawk on 2006-02-25
Ok for whatever it is worth

seems I  found a unhappy solution
reinstalled Ubuntu overwriting kubuntu install partition 
(due to frustration)
(didn't seem to help)
then 
I re-enabled the intel motherboard sound card (ac97)
 left the Creative Labs Audigy 4 alone 
on Ubuntu startup it shows enabling ALSA 0 and ALSA 1 
rebooted and attached my my speakers to the AC97 output
  and presto chango
 sound works
can't Use my Fancy Audigy 4 sound card but I do have sound
Oh well,........

---

