---
title: "No sound, Intel HD Audio, Toshiba laptop,  and Feisty"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by hondaman on 2007-05-15
Ive gone through as many pages as I can, and I am failing at making ANY sound work.  I have a toshiba p105-s9337

I have tried different lines at the end of alsa-base (auto, 3stack,laptop-ea[d, ref, etc).

I have compiled and installed the latest alsa software.

I have checked in alsamixer to make sure its not muted.

I get no sound in anything.  On startup.  In mp3's.  In preferences-> sound testing.

I have tried different mixers and different audio devices.

lspci says:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Can someone possibly have an answer to make my sound work?

Thanks!

---

### Post by rase on 2007-05-15
hi,
i have same problem, but i have some sound, but it is very quiet. when i solve it, i will let you know. i post my problem as "sound so quiet"
bye

---

### Post by chewjoel on 2007-05-17
I'm having the same problem too.
Would let you know if any progress with mine.
My posting is here: [http://ubuntuforums.org/showthread.php?t=441823](http://ubuntuforums.org/showthread.php?t=441823)

---

### Post by Arry on 2007-05-17
I'm with you guys, got sound out of my external speakers but it's incredibly quiet at top volume (you can barely even hear it, but on my windows partition it hurts my ears), and the volume dial on the front of the laptop (toshiba satellite pro p100) doesn't work at all. I've tried everything I can find, but no joy.

p.s. Without the external speakers I get no sound what-so-ever.

---

### Post by hondaman on 2007-05-17
[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

That fixed my sound problem.

---

### Post by hondaman on 2007-05-17
Oh, and my sound was really quiet too, until I figured out there was a volume wheel on my laptop.  turned it up, and now I have sound.

---

### Post by robo-linux on 2007-07-03
Hi Hondaman

I have the exact same Toshiba laptop P105-s9337 with no sound running Feisty. Can you tell me what custom DSDT file you used please?  Also did you have to rename the file to a .aml  All the DSDT files come as .asl  files.

Any help would be extremely apprecated. 

Thank you.

---

### Post by mbaker1965 on 2007-10-13
82801G (ICH7 Family) High Definition

Me too.. God damn linux.. Sure is no real plug and play features for the most common devices.

I can't get mine to work either. I tried everything.. Seriously pissing me off. No sound = no linux. Means back to Microsoft, at least Microsoft works.

Mel

---

