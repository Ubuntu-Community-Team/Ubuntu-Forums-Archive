---
title: "MEncoder skipping 1/4 of All Frames"
date: 2009-12-19
forum: Multimedia Software
---

### Post by jephthah on 2009-12-19
I'm encoding from .VOB to h.264 without any filters except cropping, and mencoder is skipping every one of every four frames for the entirety of several (but not all) of my encodings.  There appears to be an issue with the audio breaking or skipping, but I don't know if its due to this.

I'm using....
mplayer dvd://01 -dumpstream -dumpfile ~/01.VOB

followed by

mencoder ~/01.VOB -ovc x264 -x264encopts bitrate=670:threads=auto  -af volume=7 -oac faac -faacopts br=128 -o 01.mp4

Two topics for questions.

1)Is this skipping a problem?  Am I losing frames that aren't truly duplicates, and is this causing my audio issue?

2)Is there a filter I should apply, or another way to fix this, should it need fixing?

---

### Post by Jose Catre-Vandis on 2009-12-19
Try using the [h264enc script]("http://sourceforge.net/projects/h264enc/files/h264enc/h264enc-9.1.1.tar.gz/download") to rip your dvds, provides a much tighter set of encoding routines and filters for encoding.

Also, if you haven't already done so, install mplayer and ffmpeg from SVN and x264 from git. Tuts for both on the forum

---

