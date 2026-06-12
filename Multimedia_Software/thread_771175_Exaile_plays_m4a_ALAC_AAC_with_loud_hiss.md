---
title: "Exaile plays m4a ALAC AAC with loud hiss"
date: 2008-04-27
forum: Multimedia Software
---

### Post by crimsontime on 2008-04-27
I've just installed Exaile on Hardy and really love it.. the problem is that it plays my ALAC m4a files with loud hisses that frequently interrupt the playback.  I have a lot of these files from when I used to use iTunes.  I can play these files just fine in Totem and Rhythmbox so I'm not sure what is causing this.  Does anyone know a solution?  Forgive me for not providing more technical details as I am still a n00b.

---

### Post by crimsontime on 2008-04-28
Anyone, Anyone?  Bueller?

---

### Post by theacoustician on 2008-04-28
Can't offer any assistance, but I can say I've noticed a similar problem with Exaile and some playback issues with mp3s.  Played through Exaile, there's a terrible SNR and some overloading it sounds like.  Played through Mplayer, the same mp3 is fine.  So its not just you.

---

### Post by crimsontime on 2008-04-30
Just in case anyone runs into this problem... It has been solved.  I posted the question to exaile dev and got this very helpful hint:

"the only difference between Exaile and Rhythmbox in terms of
playback is in Exaile's use of the GStreamer equalizer. Try running
"exaile --no-equalizer" and see if that solves the problem."

---

### Post by theacoustician on 2008-04-30
> **crimsontime said:**
> Just in case anyone runs into this problem... It has been solved.  I posted the question to exaile dev and got this very helpful hint:

"the only difference between Exaile and Rhythmbox in terms of
playback is in Exaile's use of the GStreamer equalizer. Try running
"exaile --no-equalizer" and see if that solves the problem."

I will have to try this when I get home.  What's the deal with the equalizer?  The sound isn't overloaded, like one might expect if the settings were pegged too high.  Its more like corruption.

---

### Post by tc7 on 2008-05-11
I had exactly the same issuel with Exaile 0.2.11 playing mp4 files. It took me some time to realise it was only with the aac format as I often play my whole collection in random mode. I haven't noticed any issues with mp3 files.

Running with --no-equalizer works perfectly. Of course it would be nice to be able to used the equalizer ...

thanks very much crimson.
Otherwise Exaile is a great player - keep up the good work.

---

