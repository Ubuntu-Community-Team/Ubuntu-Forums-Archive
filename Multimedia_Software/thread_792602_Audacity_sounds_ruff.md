---
title: "Audacity sounds ruff"
date: 2008-05-13
forum: Multimedia Software
---

### Post by rab4567 on 2008-05-13
I finally got audacity working using jack, but the sound coming out stutters and is  full of static. Any ideal whats going on?

---

### Post by luctor on 2008-05-13
How did you manage to get it running with jack ?

---

### Post by aeiah on 2008-05-13
could be something to do with either your volume being too high (set your pcm and such to around 80%. i get distortion at max), or it could be to do with the sample rate perhaps? are you using 44,100 or 48,00

---

### Post by rab4567 on 2008-05-13
OK I got it working, first I think there is no one way to fix the audacity playback issues in linux, but here is my jounrey.
[B]
JACK[/B]
 * Install jack control from add/remove
 * Click on setup go to the misc tab check the start jack 
   audio on application startup.
 * Install libjack0 0.109.2 from synaptic but the audio
   was terrible.
 * I uninstalled every thing but libjack0

**ALASA-OSS**

 * I use sudo apt-get install alsa-oss that worked on my
   HP AMD 4200 2GB Nvidi 6150LE

---

### Post by rab4567 on 2008-05-13
Then again its simple on other computers just look at my acer 1GB AMD 4400 nvidia6100 setup audacity plays great.
I guess it all depends on the hardware.

---

### Post by itsme_n8 on 2008-05-16
I get great sound out of everything except Audacity and ReZound.  Actually, I get nothing out of them, and I'm not sure where to start to get it working.  They both edit great, and the final product sounds great, but that means I have to make the changes, export, then play in RhythemBox.  kinda lame.  Any thoughts, or posts that I missed that addresses this?

Ubuntu Hardy 64bit.

Nate

---

