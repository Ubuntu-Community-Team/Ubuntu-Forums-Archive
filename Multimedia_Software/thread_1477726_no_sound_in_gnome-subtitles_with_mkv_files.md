---
title: "no sound in gnome-subtitles with mkv files"
date: 2010-05-09
forum: Multimedia Software
---

### Post by plh on 2010-05-09
hi!

I got a problem with gnome-subtitles when I try to sync an srt file with an mkv file: no sound available, whereas in the case of an avi file no problem of course... :confused:

Did you experiment the same problem and find a workaround?

Thx in advance! :)

---

### Post by plh on 2010-05-31
Hi,

to whom it may concerns: I found the solution tothe problem: one of the gstreamer extension packages was missing, and gnome-subtitles systematically uses gstreamer (found no way to make it use any other tool) ! ;)

---

### Post by ryu kun on 2012-03-10
Same problem with avi file in Lubuntu 11.10 is solved after I've installed following packages through Synaptic:

gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3

---

