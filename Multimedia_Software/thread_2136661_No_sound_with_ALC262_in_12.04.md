---
title: "No sound with ALC262 in 12.04"
date: 2013-04-18
forum: Multimedia Software
---

### Post by ulukai08 on 2013-04-18
Hello,

I have a Tyan S7025 motherboard with an ALC262 chip. To get the sound working in Ubuntu 10.04 I had to do this: [http://ubuntuforums.org/showthread.php?t=1542375](http://ubuntuforums.org/showthread.php?t=1542375)

Problem is now that i switched to 12.04, when I type: 

zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

i don't have hp-rp5700     HP RP5700 anymore

but i have:

ALC262
======
  N/A

Anyone managed to make it work ?

Thanks !

---

### Post by cortman on 2013-04-18
Perhaps the ALC262 module has been fixed in later kernel versions? Have you **tried** your original fix yet? It may work.

---

### Post by ulukai08 on 2013-04-22
My original fix ?

---

### Post by cortman on 2013-04-22
> **ulukai08 said:**
> My original fix ?

Followed the instructions on the link you gave, that you said fixed it for you before.

---

### Post by ulukai08 on 2013-04-23
Oh yes of course, but still no sound. I tried hp-rp5700 even if it is not in the list, i also tried some other models without success :(

---

### Post by cortman on 2013-04-23
Ah, I see. Looks like there's a bug about it [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/998743"), and it seems someone has found a workaround using pavucontrol. Give it a try and see what happens.

---

### Post by ulukai08 on 2013-04-24
> **cortman said:**
> Ah, I see. Looks like there's a bug about it [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/998743"), and it seems someone has found a workaround using pavucontrol. Give it a try and see what happens.

Thanks !! Gonna try it tomorrow :>>

---

### Post by ulukai08 on 2013-04-26
I've tried  both solution, but still no sound :((

---

