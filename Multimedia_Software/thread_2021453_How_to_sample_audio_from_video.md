---
title: "How to sample audio from video?"
date: 2012-07-09
forum: Multimedia Software
---

### Post by Futant on 2012-07-09
Hello, as the title says I want to take audio samples from various vits of video, but cannot seem to work it out. I am running Precise, and have Specimen, which only seems to be able to sample from audio sources. I have tried with Blender which mekes it easy to isolate the audio, but I can't seem to save audio files in Blender. I know there must be a way to do this, but really need some help finding out how! Anyone?

---

### Post by evilsoup on 2012-07-09
If you're ok with the commandline, and assuming that you only have one audio track, then

avconv -i input.avi -vn -acodec copy output .mka

will give you an audio track, which you should then be able to open with specimen or whatever.

I've put .mka because that will support any audio stream; if you are using MP4 files, they probably have AAC streams, so you can use M4A or MP4 which would more likely be compatible.

---

### Post by blueshead on 2012-07-09
You can demux the video in VLC to get the audio..

---

### Post by Futant on 2012-07-13
Thanks for your help, not been able to get online in the last couple of days. I will give both of these options a whirl and possibly post a few more questions about it soon.

---

### Post by Futant on 2012-07-17
VLC is brilliant! All this time I had no idea that you can use it for that, and its so easy. Solved!

---

