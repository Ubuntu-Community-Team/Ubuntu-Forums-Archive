---
title: "libxine1-ffmpeg conflicts with players"
date: 2009-05-16
forum: Multimedia Software
---

### Post by NanaSaw on 2009-05-16
just got jaunty installed and was having a hard time getting amarok 2 to play mp3 files.It just keeps skipping through track after track when the play button is clicked.
Got libxine1-ffmpeg installed and amarok was able to play mp3 files,but vlc,totem and rythmbox no longer work.Uninstalled libxine1-ffmpeg,and amarok stopped working and now everything else works.
Need help desparately,really love the new amarok

---

### Post by gandaran on 2009-05-16
> **NanaSaw said:**
> just got jaunty installed and was having a hard time getting amarok 2 to play mp3 files.It just keeps skipping through track after track when the play button is clicked.
Got libxine1-ffmpeg installed and amarok was able to play mp3 files,but vlc,totem and rythmbox no longer work.Uninstalled libxine1-ffmpeg,and amarok stopped working and now everything else works.
Need help desparately,really love the new amarok
totem and rythmbox use gstreamer codecs (only totem-xine uses libxine1-ffmpeg) gstreamer and libxine1-ffmpeg codecs are quite deferent and I doubt they can conflict (I have all of them plus w32codecs installed with no problem) the problem must be due to something else.

---

