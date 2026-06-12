---
title: "Avidemux fails to encode audio"
date: 2012-01-26
forum: Multimedia Software
---

### Post by Rtedmonston on 2012-01-26
I've been trying to use Avidemux to convert .avi's to DVD MPEG-2 since DeVeDe quit working a few weeks ago for me with no solution in sight. The problem I'm having with Avidemux is it  seems it doesn't want to decode/encode audio, regardless of format. All my converted video files come out with the picture just fine, only no sound, I notice when I start a conversion job it shows: audio codec: None no matter what I select. Are they not enabled or something? I'm sure I have the latest version. I'm under Ubuntu Version 11.10 (Oneiric). 

Anyone have experience working with this utility program?

---

### Post by flemur13013 on 2012-01-26
I use avidemux quite a bit; haven't had your problem, but other funny things have happened when trying to update libraries.

Try avidemux -> Help -> Plugins ->Audio & Audio Decoders (tabs)
I have 6 'Audio' and 7 'Audio Decoders'.

Does avidemux play sound when you play the file?  If so, I'm pretty sure that means it has the decoders.

If you don't see any encoders/decoders - or even if you do - you might try $ synaptic -> "Complete Removal" of all the avidemux components (or "$ sudo apt-get purge avidemux"), then reinstall them.

---

### Post by cchou on 2013-01-05
I had the same issue with audio encoder showed up none when I tried to output to mp4. The video plays with sound in avidemux so I don't know what is going on. Output as avi also didn't work and I finally just used mkv. I can see that my audio is AC3 48khz 192bps which is fairly typical. mkv ends up the same size as the original dvd.

---

