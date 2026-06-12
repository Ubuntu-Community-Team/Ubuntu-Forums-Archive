---
title: "Merge mp4 using gui"
date: 2011-01-09
forum: Multimedia Software
---

### Post by primetime34 on 2011-01-09
I have multiple mp4 files that I want to merge into a single video.  I don't want to re-encode them at all, I just want to merge them together.  I understand there might be some command-line methods, but I really want to use a gui.  Any suggestions?

---

### Post by lovinglinux on 2011-01-09
Get mkvtoolnix-gui.

Open the first video with it, then click append and select the other videos, then click "Start Muxing". It will generate a mkv file with all videos merged together. No re-encoding necessary. It is pretty fast.

---

### Post by BicyclerBoy on 2011-01-09
Depending on what the file container is you can just "cat" them together..
This can cause transition glitches because of multi frame encoding.
VOBs can be "catted" together because they are a transport stream.

The mp4 doesn't really define the file container/format well enough..

You can use mediainfo or ffmpeg VLC etc to reveal this info.

---

### Post by chaceos on 2013-03-16
Is this thread solved??

---

### Post by howefield on 2013-03-16
Old thread closed.

---

