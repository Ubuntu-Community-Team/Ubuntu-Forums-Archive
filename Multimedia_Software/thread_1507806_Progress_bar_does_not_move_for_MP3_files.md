---
title: "Progress bar does not move for MP3 files"
date: 2010-06-12
forum: Multimedia Software
---

### Post by QuirkHammett on 2010-06-12
Hi all, 
this is my very first post on the ubuntu forums. i am using Ubuntu Studio for the past 3 months, without ever having to revert to Windows for ANYTHING at all (that used to be my primary OS for years now).

Anyway, i began with Ubuntu Studio 9.10 3 months ago, and almost everythign was perfect.
But last month i did a fresh install of 10.04 LTS, and realised that in Movie Player, and Banshee player the progress bar does not move whenever i play Mp3 files. for wav files, there is no problem, neither for avi files.

Could you guys help me out in locating this problem, and possibly rectify it?

Most pleased upon discovering Ubuntu Studio for my musical needs.

---

### Post by boombox1387 on 2010-06-13
> **QuirkHammett said:**
> Hi all, 
this is my very first post on the ubuntu forums. i am using Ubuntu Studio for the past 3 months, without ever having to revert to Windows for ANYTHING at all (that used to be my primary OS for years now).

Anyway, i began with Ubuntu Studio 9.10 3 months ago, and almost everythign was perfect.
But last month i did a fresh install of 10.04 LTS, and realised that in Movie Player, and Banshee player the progress bar does not move whenever i play Mp3 files. for wav files, there is no problem, neither for avi files.

Could you guys help me out in locating this problem, and possibly rectify it?

Most pleased upon discovering Ubuntu Studio for my musical needs.

Hey, welcome to the forums!  It sounds like your system is missing the codec that allows seeking in mp3s.  If you open up Synaptic and search for 'gstreamer' which plugins do you have installed?  You'll want to make sure that '-plugins-good', '-plugins-bad', and '-plugins-ugly' are all installed.  My personal guess is that you have -ffmpeg installed, which can play mp3s, but you don't have -plugins-ugly, which lets you seek in them (and should make the progress bar move).

If this doesn't fix your problem, be sure to report back, and I'll see if I can come up with something else. :)

---

