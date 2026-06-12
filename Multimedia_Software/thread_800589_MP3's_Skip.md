---
title: "MP3's Skip"
date: 2008-05-20
forum: Multimedia Software
---

### Post by vorgusa on 2008-05-20
I have tried both Totem and Rhythmbox and they both skip at the same points. Is this a problem with my file or something to do with my OS. I have played them on Windows in the past and they have worked fine. I am using ubuntu 8.04

---

### Post by mahuyar on 2008-05-20
Hard to tell.  Most likely a section of the data stream got corrupted while copying.  How do those players perform on other mp3 files?

---

### Post by Gumpy on 2008-05-20
I suspect gstreamer. Using Amarok with the libxine1-ffmpeg package solves this problem for me. (I'm still using Ubuntu 7.10 and assuming that package name hasn't changed.)

---

### Post by vorgusa on 2008-05-21
cool, I will give it a try when I get home tonight...

---

### Post by frunze on 2009-05-22
I have exactly the same problem with Ubuntu 8.04 - it skips mp3 files in ANY player: Rhytmbox, VLC,.. 
I usually work and listen to music and this is really annoying and frustrating, since playing mp3 is a really basic task that Windows 98 could do out of the box, and here we are 10 years after still not being able to properly play them.

Technical Information:

$ lspci |grep -i audio
02:06.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

VLC media player 0.8.6e Janus (wxWidgets interface)

Ubuntu 8.04 (LTS) Hardy Heron

EDIT: I installed gxine player 0.5.901 (from repositories) and it doesn't skip anymore!!! Hopefully it stays this way :D

---

