---
title: "mp3 profile in sound juicer"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by rlcate on 2007-01-20
I installed the gstreamer lame package and in sound juicer created the mp3 profile per the help file, but I get the "could not link pipeline" error when I try to extract from CD to mp3.

GStreamer Pipeline:  audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux

The lame package installed with no errors.  What am I doing wrong here?

---

### Post by po0f on 2007-01-20
rlcate,

Shouldn't the exclamation marks "!" be pipes "|"?

---

### Post by benson444 on 2007-01-20
No, they definitely should be exclamations. My pipeline reads

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux

Maybe you haven't installed one of the needed gstreamer plugins (ugly-multiverse and so on) or installed id3. That's all you should need I think.

---

### Post by rlcate on 2007-01-20
I had missed the multiverse when I installed the plugins.  Everything is working like a dream!  Thanks to all....:D :biggrin:

---

