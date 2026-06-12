---
title: "[SOLVED] Repairing broken OGG/Vorbis files"
date: 2008-10-18
forum: Multimedia Software
---

### Post by Blutack on 2008-10-18
I was in a rush, and recorded something rather critical from my video capture device in Cheese.
Cheese (or probably GStreamer...) created a nice corrupt little OGG/Theora file which will (just about) play but sends FFMpeg into a mad memory eating lockup, won't encode at the correct size in Mencoder and creates corrupt files when transcoded with VLC.  I need to convert it into a sensible format - does anyone have any suggestions as to either:
ways to repair it first so I use Mencoder/FFmpeg
or
more forgiving encoders that can output an mp4/xvid/divx file?

The archives are full of avi repairers but nothing for ogg/theora.

Thanks in advance!

---

### Post by Blutack on 2008-10-18
Never mind, I eventually managed to persuade VLC to create an decent mp4.
God free file formats are annoying.

---

### Post by Bostonian on 2009-06-23
mind sharing your solution? I'm having the same problem.

---

### Post by jlukescott on 2012-10-14
> **Blutack said:**
> Never mind, I eventually managed to persuade VLC to create an decent mp4.
God free file formats are annoying.


I am using the VLC GUI to fix .ogv files by selecting View > Advanced Controls, which adds a Record button on the main toolbar. Then, transcoding can be done by pausing a video at 0:00, pressing record, and then pressing play. The transcoded videos get dropped into your system's default "videos" folder (as set in ~/.config/user-dirs.dirs).

---

### Post by nothingspecial on 2012-10-14
Old thread.

Closed.

---

