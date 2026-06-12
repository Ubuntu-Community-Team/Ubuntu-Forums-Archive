---
title: "Soundconverter issue: 'lame' element not found, disabling MP3"
date: 2013-03-12
forum: Multimedia Software
---

### Post by ivotkl on 2013-03-12
Hello everyone, I'm trying to lower the bitrate of some MP3s files I've ripped before. The thing is that I don't have a ODD to rip the songs again to a lower bitrate.I'm using Sound Converter with lame and ffmpeg codecs related to gstreamer. I get the following error when opening the program from terminal:```
SoundConverter 1.4.4  using Gstreamer version: 0.10.30, Python binding version: 0.10.19  using gio  'lame' element not found, disabling MP3.  'faac' element not found, disabling AAC.  using 1 thread(s)
```Any help would be highly appreciated. I've searched online, this forum and other forums and had no luck. Everything I've tried pointed to installing codecs I already have installed.Running Debian, Kernel Version 2.6.32-5-486 (Mon Feb 25 00:22:26 UTC 2013), i686.

---

### Post by mc4man on 2013-03-12
Some of this may be redundant, doesn't matter. To get all those disables to go away
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly \
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg
```

---

### Post by ivotkl on 2013-03-12
Thank you very much for the prompt response. I've already have those installed (not sure if all of them) and they still won't appear on soundconverter.

Anyway, I think I'll run ffmpeg commands directly from terminal instead. If I manage with that one, I'll mark thread as solved.

---

### Post by mc4man on 2013-03-12
Sorry - didn't quite notice you're asking about Debian
On Ubuntu lame in soundconverter is provided by gstreamer0.10-plugins-ugly, faac by gstreamer0.10-plugins-bad-multiverse

May be different in Debian, look for gst plugins that deb on libmp3lame* for mp3 & libfaac* for faac (libmp3lame0, libfaac0 here in Ubuntu

---

### Post by ivotkl on 2013-03-20
mc4man, thank you for the reply. However, Situation has been solved by completely removing soundconverter. Plugins were already installed, so all I needed to do was to install it back again and it is working OK.I'm thinking that maybe plugins needed to be installed beforehand, so when new installation was done the plugins were recognised.

**Edit:** Unable to mark as solved. Where did the option go to?

---

