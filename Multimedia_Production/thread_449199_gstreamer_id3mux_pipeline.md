---
title: "gstreamer id3mux pipeline"
date: 2007-05-20
forum: Multimedia Production
---

### Post by richcoosa19 on 2007-05-20
I have a Sansa e260 mp3 player that works best when using id3 v1.1 tags.  When using the pipeline that most people recommend:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3mux

a v2.4 ID3 tag is produced in the mp3 which the Sansa refuses to read.

I modified the pipeline to be:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3mux name=tag,v1-tag=1,v2-tag=0

But it still does the same thing, a v2.4 is produced.  Any recommendations?  I read up in gst-inspect id3mux | less and this is the pipeline I came up with it...

Thanks,
Richie

---

### Post by richcoosa19 on 2007-05-20
> **richcoosa19 said:**
> I have a Sansa e260 mp3 player that works best when using id3 v1.1 tags.  When using the pipeline that most people recommend:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3mux

a v2.4 ID3 tag is produced in the mp3 which the Sansa refuses to read.

I modified the pipeline to be:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3mux name=tag,v1-tag=1,v2-tag=0

But it still does the same thing, a v2.4 is produced.  Any recommendations?  I read up in gst-inspect id3mux | less and this is the pipeline I came up with it...

Thanks,
Richie
FIXED!!!! FINALLY!!!!:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=160 ! id3mux name=tag v2-tag=false v1-tag=true

---

### Post by maubp on 2007-05-21
Hmm - can you get it to do both with this?

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=160 ! id3mux name=tag v2-tag=true v1-tag=true

I have found my in car mp3 CD player doesn't read ID3 v2.4 tags, so including v1 tags would be great...

---

