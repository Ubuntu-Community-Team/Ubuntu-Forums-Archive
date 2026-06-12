---
title: "Soundconverter Freezes"
date: 2012-02-05
forum: Multimedia Software
---

### Post by fisherm on 2012-02-05
This issue just popped up one day, and I can't think of anything that I upgraded or changed. It work one day, and then it didn't. I've done a fresh install of 10.04, and even switched to Linux Mint 9 (10.04 based). Originally, I had a pretty vanilla system with ubuntu-restricted-extras installed along with soundconverter...and that worked fine, until it didn't. It happens with any type of original file, or destination file. 

The process...I open soundconverter, open a file, it loads into the queue fine, then when I press "Convert" soundconverter goes into "freeze mode"...the window grays out, and it just sits...indefinitely. Here's the output from the terminal running "soundconverter -d" for debugging.

XXX@XXX ~ $ soundconverter -d
SoundConverter 1.4.4
  using Gstreamer version: 0.10.28, Python binding version: 0.10.18
  using gio
  using 4 thread(s)
launching: 'giosrc location="file:///home/XXX/Desktop/XXX.mp3" ! typefind name=typefinder ! fakesink'
found_type XXX.mp3
launching: 'giosrc location="file:///home/XXX/Desktop/XXX.mp3" name=src ! decodebin name=decoder ! fakesink'
TagReading done...
pipeline already stopped!
Queue done in 0s
Queue done in 0s

---

### Post by inobe on 2012-02-05
go to the main site and post a bug report.

till then there are many other apps, winff, audacity.....

---

