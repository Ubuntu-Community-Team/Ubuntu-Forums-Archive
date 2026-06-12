---
title: "Ripping a CD using Rhythmbox"
date: 2012-11-05
forum: Multimedia Software
---

### Post by gmseed on 2012-11-05
Hi

I have a CD that I've tried ripping on 2 laptops: 1) a 12.04LTS 32bit Ubuntu and 2) a 12.10 64bit Ubuntu.

In both cases the ripping gets stuck at the same track [track 13] on the CD. At which point I have to kill the application.

On one of the laptops I have Win7 installed and ripped the CD no problem using Windows Media Player.

What I don't get is that if there was a problem with the CD [eg; scratch] then wouldn't this cause problems using both Rhythmbox and MediaPlayer since the hardware is the same in both cases?

Also, is there some way of tweaking Rhythmbox to guarantee ripping the CD?

Graham

---

### Post by The Cog on 2012-11-05
Could there be a strange character in the track name that's causing issues creating the filename?

I tend to use asunder - you could give that a try instead of Rhythmbox.

---

### Post by gmseed on 2012-11-05
The filenames of the file and the before/after tracks all look ok.

---

### Post by VanillaMozilla on 2012-11-05
In Linux a CD is just like any other drive.  Did you try just copying the file?  As far as I know, you shouldn't need a separate program to "rip" a CD.

---

### Post by gmseed on 2012-11-05
Hi

I'm able to copy the file from the CD, which is in .wav format and ~48MB on disc.

Ripping such files allows them to be reformatted to .mp3, etc and reduces the file size by 1/10th to ~4MB.

Maybe Rhythmbox is locking up in doing the .wav-->mp3 encoding?

I installed Asunder and it extracts and encodes the guilty file to both .ogg/mp3 formats ok.

Does anyone know if Rhythmbox dumps errors to a log file?

Graham

---

### Post by VanillaMozilla on 2012-11-05
Ripping *is* copying, and optionally compressing in the same operation.

OK, let's restate the problem so it's clear.  Apparently Rhythmbox hangs when you import a CD directly to .mp3.  So your problem is with Rhythmbox.

You also stated that Asunder works, so the problem is likely to be in a library that Rhythmbox uses.

I can't solve your Rhythmbox problem directly, but as a workaround, I would suggest just copying the CD first and then importing into Rhythmbox.  If necessary, you could also use a second program to do a batch compression on all the files.

---

