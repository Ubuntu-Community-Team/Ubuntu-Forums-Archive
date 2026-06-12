---
title: "FFMPG Error"
date: 2009-01-21
forum: Mythbuntu
---

### Post by Senkoboy on 2009-01-21
When using Myth Archive if I try to re-encode the video it will give me  (Failed while running ffmpeg).  If I select do not re-encode it will work.  I am running a PVR 150 to record and Ubuntu 8.10 64bit with Myth backend and frontend installed. Any Ideas?

Mike.....

---

### Post by FakeOutdoorsman on 2009-01-21
I have no experience with Myth Archive, and without seeing any ffmpeg errors or encoding settings, I would guess ffmpeg is attempting to encode to a restricted format.  Try installing the **libavcodec-unstripped-51** package which will enable some restricted encoders in ffmpeg.  Purely a guess unless you can give more info.

---

### Post by Senkoboy on 2009-01-21
I think that did the trick!
Thanks, Mike

---

