---
title: "Headphone jack sense missing with snd_hda_intel"
date: 2011-09-19
forum: Multimedia Software
---

### Post by didi28 on 2011-09-19
Hi,

on a fresh install of natty with all updates, headphone jack sense is working correctly in the sense that the internal speaker turns off when I plug in headphones, but I don't see a switch where I could control this manually.

On other machines I have a switch called "Headphone Jack Sense" in alsamixer, but not on this machine.

I would like to use a email notification script I wrote also on this machine. The script turns off headphone jack sense, plays a notification sound and turns headphone jack sense back on again. This is for a shared office, where I generally use headphones for sound, but still want an acoustic email notification.

Here's the result of a ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```[http://www.alsa-project.org/db/?f=9904b9469db18e01eda6a056af8d281c060c7eb3](http://www.alsa-project.org/db/?f=9904b9469db18e01eda6a056af8d281c060c7eb3)

Thanks for help

EDIT: Wow, I just noticed this is my first post. It feels like I've been using Ubuntu Forums forever. Seems that up to now I always found what I was looking for in other people's threads... :)

---

