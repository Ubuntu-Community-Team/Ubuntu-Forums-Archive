---
title: "Sound problem"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by ShaneOMyNameO on 2007-11-30
I've had Ubuntu for a few days and after solving a few issues, I only seem to have one left: my sound; or to be more accurate, the lack of it.

It works fine in Vista, but all is silent in Linux world.

I don't know what information is needed to solve this, but I can say that the lspci command in the terminal returns

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

Also, "Conexant" has something to do with it as well


Thanks a lot for any help

---

### Post by ShaneOMyNameO on 2007-11-30
The card is HDA NVidia and the chip is Conexant CX20549 (Venice)


If it means anything, the sound actually worked when I booted from the Live CD, but doesn't work in the actual install.

Thanks

---

### Post by wesley_of_course on 2007-12-01
Morning !  Sorry about the sound issue ;

  Have you checked with alsamixer in the terminal to see if anything is muted ?

  And turned up your volumes ? Hope this will help . Keep searching tho this is somewhat common for some , I had this challenge when I installed too .

---

### Post by picopir8 on 2007-12-01
I think I have the same problem.  I changed my sound to OSS and now some applications work but nothing through firefox.

---

### Post by baxterdog on 2007-12-01
Researched the heck out of this one too. Rather than trying to see if you need a driver, try playing with the sound properties first. I can't believe how plug and play 7.10 is. Spent many hours with the alsa site and other things but found that it was already working, just not enabled correctly.

Open Volume Control --> Edit --> Preferences and then check every box, especially <b>Surround</b>. Then go back to the mixer control, unmute, and turn up the volumes. I eventually unchecked most of them again after finding the right combo for my laptop.

---

### Post by Unterseeboot_234 on 2007-12-01
I LOST my sound after a fairly recent update. What fixed me was in a terminal:

```
alsamixer
```

The terminal then turns into a 8-bit graphic display (like an old DOS game). Use your arrow keys to change the features of that sound card that you say Hardware Information echos.

I found the HDA chip on the nVidia adequate for all my multimedia. I don't play games. From the vast docs and HowTos for Cinelerra, I learned the OSS libs were the original 32-bit sound available for Linux. If I'm outputting composited multi-tracks audio for a video back to tape, I have to set the options to OSS and have faith the ia32 is still connecting all the 64-bit to 32 bit (Even though Cinelerra is the ONLY software I've used that edits the sound in 64-bit, floating-point). While I'm massaging video that is on the hard drive, ALSA or OSS will work.  Many games have to have the bridge to the OSS. ALSA is a wrapper for many things.

---

