---
title: "SOS! No sound in Ubuntu 9.04 64 bit on 965P-DS3 (Realtek ALC888 onboard)"
date: 2009-07-21
forum: Multimedia Software
---

### Post by bhanja_Trinanjan on 2009-07-21
Tried all the options in ALSA and OSS… nothing works… no sound!

---

### Post by Corsu on 2009-07-21
Hi, 

I had the same problem, then I tried to change the alsa-base.conf with all the "options" I could find.
Finnaly I found a post which is in french but I can translate it's not so long and difficult.
So at first you have to create the file alsa-base

```
*sudo gedit /etc/modprobe.d/alsa-base*
```This file is empty but just put the following line in it:

```
options snd-hda-intel probe_mask=1
```Finally just reboot and it should be working, your sound volume must be much stronger.

Regards

---

### Post by bhanja_Trinanjan on 2009-07-21
> **Corsu said:**
> Hi, 

I had the same problem, then I tried to change the alsa-base.conf with all the "options" I could find.
Finnaly I found a post which is in french but I can translate it's not so long and difficult.
So at first you have to create the file alsa-base

```
*sudo gedit /etc/modprobe.d/alsa-base*
```This file is empty but just put the following line in it:

```
options snd-hda-intel probe_mask=1
```Finally just reboot and it should be working, **your sound volume must be much stronger.**

Regards

It's not a question of low volume, there is no sound at all! :P

How does a volume fix work here?

---

### Post by Corsu on 2009-07-21
Hi, 

I thought it was no volume at all for my case too, but after when I put my volume level at max on the volume controler and on my speakers I had a very low sound. I don't even remember if the jack was connected on the front jack or the rear green jack.

But even if you don't have any sound, it's worth trying ...

---

### Post by igorzwx on 2009-07-21
aplay -l

man aplay

---

### Post by martinbaselier on 2009-07-21
I you use alsa, try starting **alsamixer** from a terminal. I had the problem on a different computer were the sound is muted sometimes and it did not show that particular mute in the panel applet. 

If you use oss, start **ossxmix**

---

### Post by bhanja_Trinanjan on 2009-07-21
Thanks... I am not absolutely sure how I did it but got audio to work... selected ALSA over Pulse/OSS and also enabled IEC958 default PCM :D

---

### Post by igorzwx on 2009-07-21
now install skype (from Medibuntu repositories)

call to a friend, and tell how it works.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

