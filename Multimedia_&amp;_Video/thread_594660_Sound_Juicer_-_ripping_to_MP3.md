---
title: "Sound Juicer - ripping to MP3?"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Michael_Grosberg on 2007-10-28
I'm having a problem with Sound Juicer. I'm trying to rip a CD to MP3 files. In the preferences dialog, you can edit profiles for rip settings, and next to it you have a drop down list to select which profile SJ actually uses.

Well, I have a profile for ripping MP3s, but it does not show on the dropdown  list. It is marked as "active", and I can remove profiles from the dropdown list by making them inactive, but I can't make the MP3 profile appear there.

What am I missing? is there an MP3 encoder package I should install? I know I can already play MP3 files.

---

### Post by GTvulse on 2007-10-29
You are missing gstreamer0.10-plugins-ugly-multiverse

---

### Post by evil_cat on 2007-11-04
:popcorn::popcorn:
Excellent I restarted my Sound juicer and it works fine for me :)

Long live Ubuntu

---

### Post by MozartlovesUbun2 on 2007-11-07
there's GOOD BAD and UGLY

do i need all 3?

---

### Post by GTvulse on 2007-11-07
If you don't want to go a-hunting for missing codecs once in a while, yes. And throw in the multiverse versions and the ffmpeg plugin to be able to watch flash video with Totem.

---

