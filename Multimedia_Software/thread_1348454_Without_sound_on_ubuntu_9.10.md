---
title: "Without sound on ubuntu 9.10"
date: 2009-12-07
forum: Multimedia Software
---

### Post by gariden on 2009-12-07
Hi there,

I don't have sound on ubuntu 9.10. Firstly I had to get the sound working, choosing analog in sound preferences. I had it for some time until a beautiful day ubuntu didn't gave out any sound. I tried many forums, but since I haven't the sound option on SYSTEM->PREFERENCES I couldn't do much about it.

My pc is a HP pavilion DV3 and has a NVIDIA CARD. Any output you need just ask please.

---

### Post by nowhere@cox.net on 2009-12-07
My SB Audigy 2 was quiet as well. I launched alsamixer in a terminal and scrolled over to turn on the analog output since only SPDIF was enabled by default. There was no option for doing this in any of the standard gnome based tools. I don't know if it matters but before I did this, I added the original admin account to the "audio" group. I had noticed that the this first account that is created at ubuntu install was not part of the group while any users I created subsequently were.

Check alsamixer if you haven't already...

---

### Post by gariden on 2009-12-07
> **nowhere@cox.net said:**
> My SB Audigy 2 was quiet as well. I launched alsamixer in a terminal and scrolled over to turn on the analog output since only SPDIF was enabled by default. There was no option for doing this in any of the standard gnome based tools. I don't know if it matters but before I did this, I added the original admin account to the "audio" group. I had noticed that the this first account that is created at ubuntu install was not part of the group while any users I created subsequently were.

Check alsamixer if you haven't already...

Thanks for ur tip. 

Unfortunately I've already tried it and it didn't work. The problem should be on pulse audio or alsa. After installing and uninstalling so many times in so many ways it gets more difficult to know what's going on, on ,my pc

---

