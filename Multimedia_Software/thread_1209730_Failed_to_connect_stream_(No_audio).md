---
title: "Failed to connect stream (No audio)"
date: 2009-07-10
forum: Multimedia Software
---

### Post by Janhouse on 2009-07-10
I get no audio in totem, gnome-sound-properties and other applications. I have working audio in VLC and I can hear startup sounds.

After opening music file with totem I got error. To get more information I ran totem thru terminal.

Any ideas?

crazy@CrazyBox:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(836): gst_pulsesink_prepare (): /GstPlayBin:play/GstBin:visbin/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin5/GstAutoAudioSink:autoaudiosink1/GstPulseSink:autoaudiosink1-actual-sink-pulse

I am using ubuntu jaunty.
Had normal audio yesterday. I have no idea what went wrong.

---

