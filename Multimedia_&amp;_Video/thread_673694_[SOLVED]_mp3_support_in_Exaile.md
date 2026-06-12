---
title: "[SOLVED] mp3 support in Exaile?"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by VoXoM on 2008-01-20
Hey,

I have the gstreamer ugly plugins installed but Exaile still won't read any mp3.
Any help?

Thanks.

---

### Post by jeffus_il on 2008-01-21
Do other Gstreamer apps work like Totem-Gstreamer?

---

### Post by VoXoM on 2008-01-21
> **jeffus_il said:**
> Do other Gstreamer apps work like Totem-Gstreamer?

Totem-Gstreamer was already installed.

So,
Exaile still won't read mp3s after the ugly plugins were installed and totem gstreamer. Also, if it can help, other programs can read mp3s except exaile.

Edit: Apparently exaile can read mp3s but not all... huh?? It managed to read a streamer rip I recorded as mp3 but it won't read any others...

---

### Post by jeffus_il on 2008-01-21
Sorry can you play mp3's with Totem, and is it the Gstreamer version?

---

### Post by VoXoM on 2008-01-21
> **jeffus_il said:**
> Sorry can you play mp3's with Totem, and is it the Gstreamer version?

Yes I can play mp3s with Totem. I really don't know why Exaile won't read them...

---

### Post by jeffus_il on 2008-01-21
OK, that means that the gstreamer libraries are correctly installed and working, we can now assume that you have an Exaile problem, which narrows down the search, maybe try a bit of googling on "exaile" "mp3" and maybe some other keywords like the error message you get, I'll also try to find something.

---

### Post by jeffus_il on 2008-01-21
Try having a look at your exaile log file, ```
less ~/.exaile/exaile.log
```

---

### Post by VoXoM on 2008-01-21
> **jeffus_il said:**
> Try having a look at your exaile log file, ```
less ~/.exaile/exaile.log
```

Thanks.

I actually found the problem.

The songs were from my MTP device and were transfered with the .b-mtp--2134703932 extention or something like that... I needed to rename the extension to .mp3 to make it work.

I have about 500 songs to rename like that... :lolflag:

---

### Post by jeffus_il on 2008-01-22
You can bulk rename with "easytag", try it.

---

