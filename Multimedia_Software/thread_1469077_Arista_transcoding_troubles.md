---
title: "Arista transcoding troubles"
date: 2010-05-01
forum: Multimedia Software
---

### Post by WillFerrellLuva on 2010-05-01
just installed arista, as it was a featured application in lucid.  Tried to transcode a dvd -> Computer - Normal (patent-free) and an error was thrown:

```

arista.transcoder.PipelineException: Unable to construct pipeline! could not link audioresample0 to vorbisenc0

```

Anybody else having trouble with this application, or know a fix?

---

### Post by drillerccg on 2010-05-14
I installed it under Lucid, was able to get it to start the very first time, but it kept looking for plug-ins. Since that fist time as, I try to start the program, it won't. Frustrating.

---

### Post by linux-michi on 2010-05-15
> **drillerccg said:**
> I installed it under Lucid, was able to get it to start the very first time, but it kept looking for plug-ins. Since that fist time as, I try to start the program, it won't. Frustrating.

I had the same problem.
First remove all:

sudo apt-get purge arista
rm -r ~/.arista

and install new

sudo apt-get install arista

greets

---

