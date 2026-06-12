---
title: "Encoding DVD with Mencoder gives spanish language"
date: 2008-06-02
forum: Multimedia Software
---

### Post by Eman1955 on 2008-06-02
It seems Spanish is the default language when I encode a DVD to .avi on my hard drive.  
Does anyone know the settings for English?  I tried the following but it did not work.

-alang English

Also the scaling does not work.  It leaves the video at default, 720x480

Complete statement for first pass:

mencoder dvd://-chapter 1-32 -vf scale=480:270 -alang English -ovc xvid -xvidencopts bitrate=800:pass=1:turbo:threads=2 -ofps 25 -oac copy -o /dev/null

---

### Post by aeiah on 2008-06-02
perhaps you're best selecting the audio channel rather than the language. you'll be able to find which is which by switching through them whilst playing the dvd

---

