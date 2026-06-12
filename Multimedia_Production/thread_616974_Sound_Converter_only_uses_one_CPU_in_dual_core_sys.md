---
title: "Sound Converter only uses one CPU in dual core systems?"
date: 2007-11-18
forum: Multimedia Production
---

### Post by Bazirker on 2007-11-18
I'm converting a ton of audio files to another format using Sound Converter and I noticed that the process is using 100% of my first core and none of my second.  Is there any way I can make Sound Converter use both of my cores when performing file conversions?

---

### Post by deadgobby on 2007-11-19
It may be that it is 32 bit program and not using  both CPU's. All so the fact that they are audio files and do not take up such resources as converting video files from one formate to the other.
Gobby

---

### Post by mcduck on 2007-11-20
> **Bazirker said:**
> I'm converting a ton of audio files to another format using Sound Converter and I noticed that the process is using 100% of my first core and none of my second.  Is there any way I can make Sound Converter use both of my cores when performing file conversions?

Sadly, no. Sound Converter doesn't have option to convert 2 files at the same time, which would be the only possible way to use both cores. Single program thread can only use one CPU (or core).

Of course you could start 2 Sound Converters (with different sets of audio files) and run them at the same time.

---

### Post by Bazirker on 2007-11-21
That's true, I suppose I could run two at a time.  Bummer that it's only single threaded, but I'll try running two instances simultaneously for larger batches.  On the plus side, it's nice to be able to use my system during encoding with a relatively low decrease in performance.

---

