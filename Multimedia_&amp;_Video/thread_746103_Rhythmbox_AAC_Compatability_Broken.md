---
title: "Rhythmbox AAC Compatability Broken"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by HangukMiguk on 2008-04-05
When I was using rhythmbox originally, AAC formats worked perfectly fine.  However, since I have switched back, they now refuse to play. MP3/Ogg still plays fine.

Also of note, AAC functionality on my system is not broken on XMMS/Audacious/VLC.

Steps I've taken to rectify the issue (in order):

1. Reinstalled libfaac0 in Synaptic
2. Reinstalled libfaad2-0 in Synaptic
3. Reinstalled Rhythmbox in Synaptic

It looks like the problem is related to the gstreamer plugin though for libgstfaad.so (according to terminal)

So I did the following steps:

4. Reinstalled gstreamer-plugins (good, bad, ugly, as well as the multiverses for each).

What am I missing?

---

### Post by HangukMiguk on 2008-04-05
Ok, I just reinstalled EVERYTHING on my system pertaining to gstreamer and/or rhythmbox.  Still not working.

Here's the exact error I'm getting from terminal:

> (rhythmbox-metadata:511): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaad.so': /usr/lib/gstreamer-0.10/libgstfaad.so: undefined symbol: faacDecDecode

Help, please?

---

### Post by HangukMiguk on 2008-04-05
bump, help.

---

### Post by HangukMiguk on 2008-04-05
Now getting this error:

**Message: don't know how to handle audio/mpeg, mpegversion(int4, framed=(boolean)true, codec_data=(buffer)1210, rate=(int)44100, channels=(int)2

---

