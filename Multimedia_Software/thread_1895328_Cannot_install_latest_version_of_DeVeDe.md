---
title: "Cannot install latest version of DeVeDe"
date: 2011-12-14
forum: Multimedia Software
---

### Post by mvandemar on 2011-12-14
I am on Ubuntu 11.04. My copy of devede keeps crashing with a very unhelpful error when I try and convert an avi, "Failed to create the DVD tree. Maybe you ran out of disk space" (which I didn't). Based on the research I did this is a generic catch-all error which was fixed in newer versions of devede. I am running DeVeDe 3.16.9. However, I cannot seem to upgrade. I grabbed the .deb from here:

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

but when I run it I get:

Dependency is not satisfiable: ffmpeg (>=4:0.7.2)

And when I try and install ffmpeg it tells me ffmpeg is already the newest version, which is:

FFmpeg version 0.6.2-4:0.6.2-1ubuntu1.1

Any suggestions on what I should do from here? Thanks.

-Michael

---

### Post by wolfen69 on 2011-12-14
You could get the latest ffmpeg by adding the ppa for it. 
```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg && sudo apt-get update
```
then 
```
sudo apt-get upgrade ffmpeg
```

---

### Post by mvandemar on 2011-12-15
> **wolfen69 said:**
> You could get the latest ffmpeg by adding the ppa for it. 
```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg && sudo apt-get update
```
then 
```
sudo apt-get upgrade ffmpeg
```

Awesome! Worked like a charm, thanks. :)

-Michael

---

