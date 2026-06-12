---
title: "Sound Juicer"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by trevorv on 2007-06-12
I wish to rip CDs into FLAC, and I wish to do so at the highest compression rate. Previously I've been using abcde (a fine, fine piece of software), but thought I'd try using Sound Juicer. However, I have no idea how to set the compression rate. Do I need to edit the GStreamer pipeline? If so, what to? Is there a good guide on GStreamer pipelines somewhere?

The current one is

```
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc
```

And finally, how can you check the compression of an existing FLAC file?

Thank you.

---

### Post by trevorv on 2007-06-13
I found the answer, so in case it's useful to anybody, you can simply add the compression option to the end of the pipeline as an option to flacenc, e.g.

```
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc quality=8
```

I'll add info to this post if I figure out how to tell the compression rate of an existing FLAC file, although I'm not convinced there is a way at all.

---

