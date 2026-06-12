---
title: "Rhythmbox making a mess of folders and file names"
date: 2010-01-08
forum: Multimedia Software
---

### Post by bluetomgold on 2010-01-08
As a new user I'd just like to say how impressed I am with Ubuntu. That said, I am learning about new bugs all the time!

I've been enjoying using Rhythmbox to rip a stack of CDs. Initially I had problems getting it to recognise Lame but following uninstalling and reinstalling it, it seemed to be working well. That is, until I looked in my Music folder.

It turns out files have been placed in individual folders, named "number - title.udio" (e.g.: "11 - She Can Do What She Wants.udio". The mp3 file itself is named identically throughout - it's the string for the gstreamer settings, i.e. "x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1002 ! xingmux ! id3v2muxmp3".

The settings within Rhythmbox's properties for folder and file naming are all set to the sensible default.

This is a pain. In the short term I'm going to try EasyTAG to sort it out, but ultimately I need to sort this or find alternative software. 

Any ideas? Cheers!

---

### Post by bluetomgold on 2010-01-08
Ok, good news and bad news. The good news is EasyTAG works. The bad news is I have to rename all the files 1st anyway because Rhythmbox didn't put a "." before mp3 in the filename. EasyTAG only recognises the files after they have been renamed.

I bet there's a really easy way of putting ".mp3" on the end of all the files via terminal, but being a total noob I have no idea. If anyone can enlighten me and save me hours of manual renaming I'd be grateful!

---

### Post by bluetomgold on 2010-01-10
Any ideas on how to "fix" rhythmbox? Or suggestions for more reliable ripping/music playing?

---

### Post by bluetomgold on 2010-02-01
Well, it turned out the settings were wrong. My mistake although I have no idea how it happened. Rhythmbox is working fine now it's correctly set.

---

