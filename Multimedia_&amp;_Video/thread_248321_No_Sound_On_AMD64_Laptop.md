---
title: "No Sound On AMD64 Laptop"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by Skizem on 2006-08-31
Hello Ubuntu Community!
I'm a long time Windows user, just recently acquired a No-OS Gateway MX3410 Notebook, and decided to give a Linux-based OS a shot, so I did some research and settled on Ubuntu.

So, I've installed it from the Live CD, got ALMOST everything working except for my audio. I've browsed through the documents here on the forums and tried a lot of console commands as per the instructions, but no matter what I try, I can't get ANY sound out of my machine.

If I go Volume Control and change device I get two options:

1) HDA Nvidia (Alsa Mixer)
2) SigmaTEL STAC9200 (OSS Mixer)

As far as I can tell, it's an nVidia on-board soundcard with a SigmaTEL chipset. Regardless, no sound. If I could get some sound out of this machine it would be great, any help appreciated. (please keep in mind this is my first Ubuntu install, so detailed instructions are best, heh)

---

### Post by rabbi1337 on 2006-09-04
I am having the same issues dual booting the mx3414 version. They both have the same audio chipset, any clarification in this would help seeing as I am a new linux user too :-)

---

### Post by darkhatter on 2006-12-29
I've got the same laptop sound doesn't appear to work, its driving me crazy I even try compiling the new 2.6.20rc2 kernel and still didn't get results

---

### Post by brandoncolorado on 2007-01-21
Same here.

---

### Post by brandoncolorado on 2007-02-04
Has anyone tried 1.0.14 RC2?  The STAC 92xx is mentioned in the documentation.

---

### Post by dsiddens on 2007-02-05
My laptop is a HP DV8000 with Ubuntu 6.06.  No sound.

---

### Post by brandoncolorado on 2007-02-12
I just read the 1.0.14rc2 change log at ALSA.  It looks like there is a partial fix already built in, and that they are working on this problem for 1.0.14 final release.  Hopefully my reading is right.

---

