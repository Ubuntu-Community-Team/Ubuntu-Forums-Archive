---
title: "How to reduce streaming quality over wifi with Mediatomb?"
date: 2015-04-26
forum: Multimedia Software
---

### Post by dani-valverde on 2015-04-26
Hello,
I've just installed Mediatomb on a Hummingboard running Ubuntu 14.04 LTS. When I stream over wifi to my TV there's a lot of lagging. I would like to know if there is any way to tell Mediatomb to compress the signal when streaming over wifi. Can you help?
Thanks!

Dani

---

### Post by Rob Sayer on 2015-04-28
Well, it's already compressed.  Almost all video other than raw camera output is, even BluRay.  Probably h.264 format.  

I tried an experiment a couple of days ago.  Took a typical video file which is about an hour long, 500MB or so, bit rate of 1000Kb/s, and converted it to huffYUV format, which is uncompressed.

The output was about 25Mb in size and the bit rate was about 55Mb/sec.

Does this service offer a choice of resolutions?  Try a downsized one.

Do you have any problems with video files in your media player?

Also "hummingboard" is a rather useless decription.  Post more hardware details like cpu, ram, and video card, which can be found by pasting this into the terminal:

```
sudo lshw -C video
```

and posting here, in [CODE] tags.

---

