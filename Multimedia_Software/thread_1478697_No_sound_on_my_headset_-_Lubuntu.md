---
title: "No sound on my headset - Lubuntu"
date: 2010-05-10
forum: Multimedia Software
---

### Post by FoxMcCloudwp on 2010-05-10
Hey guys, I just installed Lubuntu on my PC. Everything is working fine except for my audio. I have no sound through my headset. I can't find a Sound configuration program on here, I went through alsamixer and it detects my Headset, but it doesn't let me switch sound devices. Anyone know how to fix this? Thanks in advance.

---

### Post by JakeLawrence on 2010-05-10
I'm having the same problem, man! I have no idea if any of the following information is compatible with Lubuntu, but here's advice I gave to another poster with the same problem:

I have the exact same problem! I'm doing research on it right now. I'll  update you if I find anything. It might help if you post the make/model  of your PC and the output of this code in the Terminal  (Applications->Accessories->Terminal):

```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

I don't know how new to Ubuntu you are, but if you're having problems  entering your password with the Terminal (like I was a couple of weeks  ago), go ahead and enter the password where the blinking bar is (there's  no visual feedback) and press enter.

---

### Post by Phenex1978 on 2010-05-10
Hello I had the problem with the last Ubuntu release on my Asus G50Vt, fixed by :

[I]**sudo vi /etc/modprobe.d/alsa-base.conf** (you can use any text editor instead of vi)

and add the line

[/I][I]**options snd-hda-intel model=m51va position_fix=0**

at the end of the file, then close and save, and restart the computer.

Maybe m51va should be modified with the specific model of your sound card.


Best regards,


Phenex
[/I]

---

