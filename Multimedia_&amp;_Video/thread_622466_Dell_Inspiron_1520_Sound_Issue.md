---
title: "Dell Inspiron 1520 Sound Issue"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by Lorac1949 on 2007-11-24
I have a dual-boot (Windows XP Pro and 7.10 Gutsy Gibbon) Inspiron 1520.  Sound works fine on Windows side, but na da in Ubuntu.  I have a High Definition Audio 2.0 sound card.

Inspiron specs:
dual core 2.2GHz 800Mhz 4M L2 cache processor
1G shared dual channel memory
250GB SATA hard drive

I know very little about Ubuntu, so please respond with clear step-by-step directions.  Any help would be appreciated.

---

### Post by linux23dragon on 2007-11-25
> **Lorac1949 said:**
> I have a dual-boot (Windows XP Pro and 7.10 Gutsy Gibbon) Inspiron 1520.  Sound works fine on Windows side, but na da in Ubuntu.  I have a High Definition Audio 2.0 sound card.

Inspiron specs:
dual core 2.2GHz 800Mhz 4M L2 cache processor
1G shared dual channel memory
250GB SATA hard drive

I know very little about Ubuntu, so please respond with clear step-by-step directions.  Any help would be appreciated.

Open up a terminal, then copy paste this command : -

```
sudo apt-get install linux-backports-modules-generic
```

Then Reboot.

---

### Post by Lorac1949 on 2007-11-25
Thank you!  That worked like a charm.

---

### Post by alexander.forster on 2007-11-26
bonus step:

open up a terminal and type in

```
alsamixer
```

then scroll over to where you can toggle between digital mic 1 and analog inputs,

analog inputs is an external plug in mic and didital mic 1 is the internal mic

enjoi!

---

### Post by waspinator on 2008-01-20
I had a similar issue, and this resolved some of it. Unfortunately the sound is very very quiet. is there anyway to make it loader?

---

### Post by tr333 on 2008-01-23
> **waspinator said:**
> I had a similar issue, and this resolved some of it. Unfortunately the sound is very very quiet. is there anyway to make it loader?

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low)

See if that fixes your low audio problem.

---

