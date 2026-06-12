---
title: "Sound problem on Intel ICH4. Sound only plays on keypress (any)"
date: 2014-03-11
forum: Multimedia Software
---

### Post by timineutron on 2014-03-11
Well, I know the title is not quite explanatory, because this is the weirdest bug/missconfiguration I've ever seen before in my life. 

So I've been trying really hard to set this really old Acer TravelMate 280 with linux, and I've succeded almost perfectly with Linux Mint 9 (xfce).
But now the problem is that whenever I want to play ANY sound from ANY application (even speaker-test from alsa), I have to press a random key for the sound to start. Just after pressing any key (in every position/window/etc) I hear what seems like the buffer filling up, for like 1 sec, and then it plays PREFECTLY. And after releasing the key, I hear what I assume it would be the buffer debuffering and then sound stops. At first I tried with a live streaming through livestreamer -> VLC, and video worked perfectly and kept on running, while audio paused every time I released the random key I was pressing (random as in even SHIFT, or Screen Capture, or ESC, or whatever). So I assumed audio just didn't come out of the speakers, but it was still being processed. But recently I've tried with Exaile, and wht it does is COMPLETELY pause the player, although it says it's still playing, but the progress bar freezes completely and the numbers showing the seconds too. After hitting a random key and keeping pressure again, it picks it up where it left, as if nothing had happened.

It's driving me nuts, mostly because it's quite insane that an audio issue has anything to do with the keyboard.

Please, excuse my poor english vocabulary, and I hope some genious out there would fancy taking a look into this problem and giving me a solution/pointing me in the right direction.

If you need any further information, anything at all, just ask.

Timineutron

---

### Post by mörgæs on 2014-03-11
Hi, welcome to the fora.

Mint 9 is obsolete. I suggest that you begin with a fresh install of Lubuntu 13.10. 
Please post back if you still have a problem with sound.

---

### Post by timineutron on 2014-03-12
Well, you know, it's an Acer TravelMate 280 from the year 2000 and I'm installing an Operating System from april 2010, so I really can't install something from 2013 into that poor PC. But thanks for the reply though :).

What I really want is understand this problem and be able to solve it, since I don't think the solution would be extremely difficult.

---

### Post by mörgæs on 2014-03-12
> **timineutron said:**
> I really can't install something from 2013 into that poor PC. 

Why is that - have you tried? 
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by timineutron on 2014-03-13
I haven't, but it was hard enough installing an OS 3 years younger than that, because I have really limited HD capacity (less than 5GB). But maybe I'll try and post back. Anyways, that's not the solution to the problem, just a clean wipe :D

---

### Post by timineutron on 2014-03-13
Well, I tried installing Lubuntu into my machine, but it won't even let me install. I tried with the booting options (acpi=off i915.modeset=1 vga=792) that currently work with my current Mint, but to no success. I think I'll just keep trying to fix the sound, or just let it be, because I've already installed the software I wanted to and I really don't want to go all the process again. If anyone thinks of something that might help to fix the sound problem, please let me know.

Best Reggards

---

### Post by Yellow Pasque on 2014-03-14
Have you considered that this might be a hardware issue?

Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

About the only thing I could see fixing it is trying:
```
options snd-intel8x0 buggy_irq=1
```
in /etc/modprobe.d/alsa-base(.conf)

---

