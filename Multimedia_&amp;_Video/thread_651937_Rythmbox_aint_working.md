---
title: "Rythmbox aint working?"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by asimmittal on 2007-12-28
Recently installed ubuntu... wanted to listen to my music files which are on my NTFS partition. I have installed ntfs-3g so I can read/write to the drive.

I wanted to play a file using Rythmbox... I tried to import a file but, then it doesnt open the mp3 files...

Checked the error log and it said GStreamer is missing... whats going on??

---

### Post by Yellow Pasque on 2007-12-28
Go into Synaptic and install all the gstreamer0.10-plugin packages, except the debug (dbg) ones. That should fix you up.

---

