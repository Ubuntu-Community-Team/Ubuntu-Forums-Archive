---
title: "gstreamer has encountered a general stream error (SoundConverter)"
date: 2010-12-10
forum: Multimedia Software
---

### Post by jiggling_john on 2010-12-10
Hi,

I've been trying to get soundconverter to work on ubuntu 10.10, I've checked I've got all the restricted packages installed, gone into synaptic and installed a bunch of gstreamer stuff, downloaded and compiled the latest version of soundconverter but whatever I do, the following happens:

1. open soundconverter
2. open file (wav)
3. set to convert to mp3 (default)
4. Click convert and instantly get the ever so helpful "general stream error" message!

any Ideas?

---

### Post by jiggling_john on 2010-12-10
if its any help, this is the terminal output:

```
davo@hp-laptop:~$ sudo soundconverter
SoundConverter 1.5.3
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
  using Gstreamer version: 0.10.30
  using gio
  using 2 thread(s)

(soundconverter:2298): libglade-WARNING **: could not convert string to type `GValueArray' for property `authors'

(soundconverter:2298): libglade-WARNING **: could not convert string to type `GValueArray' for property `documenters'
/usr/local/bin/soundconverter:2788: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  glade = gtk.glade.XML(GLADE)
Queue done in 0.008s (1 tasks)
error: GStreamer encountered a general stream error. (audiotrack.wav)
error: GStreamer encountered a general stream error. (audiotrack.wav)
Queue done in 0.011s (1 tasks)
Queue done in 1.231s (1 tasks)

```

---

