---
title: "How to remove soundcard from ALSA?"
date: 2008-10-29
forum: Multimedia Software
---

### Post by magichours on 2008-10-29
Hello all,

I'm after some help on removing a soundcard so ALSA no longer has it listed.

Background:-
Basically I have a SB Audigy 2 (emu10k1) installed, which I make use of, and a Via VT8237 integrated soundcard that I never use. ALSA keept switching between the two which is most frustrating! I followed all the guides I can find on how to store the settings, but nothing has worked! It seems completely random when it switches, sometimes I'll reboot 5 times and it'll be fine. Other times it will only last for 1 reboot.

I recently upgraded to 8.10 and am still experiencing the same problem. Also Flash audio has never worked for me and I suspect it may be trying to use my VIA soundchip (as everything else seems fine).

**All I'm after is some instruction on how to completely remove any reference of the VIA integrated soundcard within ALSA**. BTW onboard audio has been disabled in the bios since before the 8.10 install (which was a clean install on a new partition)

Please help guys, this is driving me nuts!!

**specs:-**
32bit Ubuntu 8.10
amd64 fx53
Asus A8V deluxe mobo - VIA K8T800 Pro chipset
1Gb Ram
nvidia 6200 agp GPU
1 300Gb Seagate h/d (XP)
1 200Gb Maxtor h/d (Ubunutu)

---

### Post by aeiah on 2008-10-29
have you tried asoundconf? run it in a terminal. you should be able to set the default card from there. ive set it up on my system to run this command at startup.
something like
```
asoundconf set-default-card cardname
```

you may have tried this though.

have you looked here on your googling travels?
[http://ubuntuforums.org/showthread.php?p=1824685](http://ubuntuforums.org/showthread.php?p=1824685)

---

### Post by markbuntu on 2008-10-29
In the first part of this guide is an explanation of this problem and how to fix it:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

