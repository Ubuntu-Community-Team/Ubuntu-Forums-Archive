---
title: "Sound loss"
date: 2009-01-01
forum: Multimedia Software
---

### Post by suggsville on 2009-01-01
I have this problem. My linux system is giving me no sound. Last night it did, i have no idea what to do. This is complicated, possibly, because my windows vista boot on the same system does give me sound. Any suggestions on what i can do? The only noise i get is a static like sound whenever i try to play anything. Any suggestions would be useful.

---

### Post by khelben1979 on 2009-01-01
Each time the kernel get's replaced by a newer one, the sound stops working because the ALSA sound system needs to be reinstalled.

Downloading all the source packages directly from [the Alsa homepage]("http://www.alsa-project.org/main/index.php/Main_Page") and then configuring up and installing these and then running [this ubuntu script]("http://ubuntuforums.org/showthread.php?t=820959&highlight=alsa+script") does the trick. This "may" not be easy for you if you're a beginner, but it is a solution.

Inside the Alsa source packages you'll see a README file which will describe how you should compile them if you don't know this b.t.w.

Good luck! :popcorn:

---

