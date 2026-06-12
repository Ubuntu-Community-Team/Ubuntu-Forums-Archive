---
title: "How do I connect 2 videos together?"
date: 2008-08-12
forum: Multimedia Software
---

### Post by orangecakez on 2008-08-12
I have 2 .avi video files, and I want to connect both of them into a single video file so that the second vid is attached to the first one, and so the entire thing plays without interruption (so there's no need to open the first one, finish watching it, then opening the second one and you can just watch the entire thing without having to open another file). How can I do this?

---

### Post by pytheas22 on 2008-08-12
You can do it from the command-line but I don't know the commands.  There are some nice GUI applications that would work just as well, though.  Cinelerra is probably the most powerful (but also the most complex).  Kino is also good, and pretty straight-forward.  And you can do some very basic stuff with VLC, which might be able to handle just stringing two videos together.

I think that Kino is in the repositories.  Cinelerra and VLC have packages for Ubuntu on their sites; find them through Google.

---

### Post by brian_p on 2008-08-12
> **orangecakez said:**
> I have 2 .avi video files, and I want to connect both of them into a single video file so that the second vid is attached to the first one, and so the entire thing plays without interruption (so there's no need to open the first one, finish watching it, then opening the second one and you can just watch the entire thing without having to open another file). How can I do this?

Transcode both .avis to something that can be concatenated, for example .mpg. Both .mpg files must have the same bitrate, frame rate etc.

```
ffmpeg -i file.avi -target pal-dvd file.mpg

```

```
cat file1 file2 > file3
```

---

### Post by orangecakez on 2008-08-12
I don't want to lose any quality though, is this possible? Not even a little bit...the quality is already bad as it is, and I don't want to lose not even another pixel

---

### Post by brian_p on 2008-08-13
> **orangecakez said:**
> I don't want to lose any quality though, is this possible? Not even a little bit...the quality is already bad as it is, and I don't want to lose not even another pixel

That sets the bar high. ffv1 and qtrle are lossless codecs; maybe they have something to offer. And this might help:

[http://ffmpeg.mplayerhq.hu/faq.html](http://ffmpeg.mplayerhq.hu/faq.html)

---

