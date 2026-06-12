---
title: "Audio file conversion software"
date: 2008-12-03
forum: Multimedia Software
---

### Post by adamitj on 2008-12-03
Does anyone knows a software for Linux / Ubuntu for audio conversion?

I need to make some extensive conversions on my MP3 library, but I need one application that can process batches of conversion (i.e.: converts all files to MP3 128 Kbps Joint-stereo).

Any suggestions would be appreciated. Thx.

---

### Post by Tilex on 2008-12-03
Lame is a command-line MP3 encoder.  

You can install it through "apt-get", and then "lame --help" will tell you how to specific the parameters (i.e. 128kbps, joint-stereo) that are approriate for you.

---

### Post by dorkdork777 on 2008-12-03
Pretty sure "Sound Converter" can do this. It's about as basic as you get, but it does it, and does it well. Very UNIX :P

---

### Post by magnus0 on 2008-12-03
install soundconverter from synaptic.

---

### Post by adamitj on 2008-12-03
Yes, soundconverter is exactly what I was looking for.

I use Ubuntu since version 7.04, but have been always focused into sw development with Java.

Thx all.

---

### Post by SuperSonic4 on 2008-12-03
I've used soundkonverter and perl audio converter mostly but both of these are for the kde desktop

---

### Post by pmcginley on 2009-01-15
> **magnus0 said:**
> install soundconverter from synaptic.

i've been trying to get sound converter working for convert to mp3, but i'm having no luck - it insists that the gstreamer plugins are not installed, but they clearly are.  if i run from terminal i get this:

SoundConverter 1.4.1

(soundconverter:28832): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstcdaudio.so': libcdaudio.so.1: cannot open shared object file: No such file or directory

(soundconverter:28832): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmms.so': libmms.so.0: cannot open shared object file: No such file or directory

[plus about a dozen more of these warnings, all about files that are clearly in the folder that this says they're not in]

  using Gstreamer version: 0.10.21, Python binding version: 0.10.13
  using gio
  'lame' element not found, disabling MP3.
  'faac' element not found, disabling AAC.
  using 1 thread(s)

i've uninstalled and reinstalled everything umpteen times, but nothing changes.  any ideas?

---

