---
title: "sound juicer aac problem"
date: 2010-01-24
forum: Multimedia Software
---

### Post by hasch on 2010-01-24
Hi! I was wondering why I couldn't get "aac" to the "format" in "preferences" of sound juicer. Have already added aac to "gnome-audio-profile" like this:
```
profile ame: AAC
profile description: aac-encoding
gstreamer: audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4
file-extension: m4a
check for active
```restarted sound juicer. Sadly to say there's no "aac-profile" in the "output-format-section"! :( Can someone please help me out?

Greets Hasch

---

