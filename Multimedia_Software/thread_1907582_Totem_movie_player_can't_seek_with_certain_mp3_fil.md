---
title: "Totem movie player can't seek with certain mp3 files"
date: 2012-01-11
forum: Multimedia Software
---

### Post by JohnElway on 2012-01-11
I just switched to Ubuntu 11.04 from 10.04. I checked out the bug reports involved with this, and the main thing I got from them was that you need to have the following gstreamer plugins installed:

gstreamer0.10-plugins-good 
gstreamer0.10-plugins-bad         
gstreamer0.10-plugins-ugly

They're all installed on my system, but the problem persists. Anybody know how to solve this?

---

### Post by gordintoronto on 2012-01-11
Have you tried playing these files with VLC? I'm not sure about MP3s, but VLC will tell you if a video file is "broken," which means you can't seek within the file.

---

### Post by JohnElway on 2012-01-11
> **gordintoronto said:**
> Have you tried playing these files with VLC? I'm not sure about MP3s, but VLC will tell you if a video file is "broken," which means you can't seek within the file.

Yes, I can seek these files fine with VLC. It's weird because some files work properly in Totem and others consistently don't. This makes me think that it does have something to do with the files, but because they work in VLC and my old version of Totem (from 10.04) I still think the actual problem is with my current version of Totem.

---

