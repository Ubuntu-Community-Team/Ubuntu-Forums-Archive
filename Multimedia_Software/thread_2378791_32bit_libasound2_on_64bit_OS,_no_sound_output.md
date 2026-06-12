---
title: "32bit libasound2 on 64bit OS, no sound output"
date: 2017-11-27
forum: Multimedia Software
---

### Post by AnttiV on 2017-11-27
Hi.

I have an ongoing battle with 32bit dosbox (daum) and 64bit OS (xubuntu 17.04). I finally managed to make it run (after a LONG trial and error period...), but now I got no sound coming out of it.

While trying to get it to install, I had to ```
sudo apt-get install libasound2:i386
``` I'm fairly sure this is the reason I got no sound out of it. 

So, the question is: What do I need to do now, to get sound out of a 32bit binary using libasound2:i386 while running a 64bit OS?

---

### Post by Dennis N on 2017-11-27
If not installed, install **libasound2-plugins:i386**

---

### Post by AnttiV on 2017-11-27
It works! Thank you!

---

