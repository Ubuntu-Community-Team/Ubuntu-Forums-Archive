---
title: "Best Program For Ripping DVD"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Majorflam on 2010-01-21
Hi,

I travel a lot and I want to convert all my DVD's to avi format so that I can play them through my media player.

K3b has an option for ripping DVD, but it doesn't seem to do anything! I've Googled for answers but to no avail.

Thanks in advance for any advice you can give.

---

### Post by howefield on 2010-01-21
Handbrake is very good, although it has dropped support for avi in the latest version. You can convert to other formats such as mp4 or mkv.

If you really want the outdated avi container, then try winff, which is basically a GUI to the excellent ffmpeg.

---

### Post by Majorflam on 2010-01-21
Handbrake works a treat, however the output filesize seems rather large. 229 Mb for roughly 7 minutes of video, is that normal?

---

### Post by howefield on 2010-01-21
Seems a large file size, just checking some of mine show about 1.2 to 1.4 gig for a 90 minute film.

Your file size would come out about 3gig for a 90 minute film.

What format are you converting to ?

Try using a different codec in Video settings.

---

### Post by Majorflam on 2010-01-21
Video codec set at h.264. I'm converting to m4v

---

### Post by howefield on 2010-01-21
Experiment with the "Constant Quality" slide control in the Video tab until you get about 120 meg for your 7 minute video, (or whatever file size you want)

---

### Post by Majorflam on 2010-01-21
Well, got that sorted by encoding mpeg4(ffmpeg). However, my sony mp4 player isn't recognising the file type, it says it's unsupported???

Thanks for all your help, by the way.

---

### Post by VertexPusher on 2010-01-21
Find out the MPEG-4 profile that your player supports, then encode to that profile. MP4 is a container, not a format. It can contain lots of different formats, and your player only supports a few of them.

---

