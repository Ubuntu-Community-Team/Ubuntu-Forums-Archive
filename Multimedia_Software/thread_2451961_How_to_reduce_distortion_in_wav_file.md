---
title: "How to reduce distortion in wav file?"
date: 2020-10-13
forum: Multimedia Software
---

### Post by marsdenf on 2020-10-13
Using clean install of xubuntu 20.04.   In a voip program called Zoiper 5,  there is an option to play a sound file upon incoming sms message.  No matter what file I choose, the sound is distorted and too loud.  (The sound files play properly with vlc or other multimedia programs).  I used sox to reduce the volume (-v) to as little as 10% of the original, but Zoiper still makes it sound distorted and too loud (no change).  What changes should be made to the wav file(s), and is there a simple, free program for linux to do it? For example, sox?

---

### Post by TheFu on 2020-10-14
There are probably 50 programs for audio file manipulation on Unix systems.  For something like this, I'd look at **audacity**, assuming the file is the issue.  But I don't think the file is the issue. I think the problem is inside Zoiper. It has the gain set too high, so until you fix that any file will sound bad.  I don't know anything about Zoiper. Never heard of it.

---

