---
title: "VOB playback is iffy"
date: 2010-06-02
forum: Multimedia Software
---

### Post by marshmallow1304 on 2010-06-02
I just learned how to rip a DVD in full quality with vobcopy.  I did
```
vobcopy -F 64 -l
```
which resulted in an approximately 5.5 GB VOB file of an approximately 1:40 movie.  The problem is that although players play the file, I haven't found a single one that works completely and properly.  In Totem, the total time jumps around, finally staying (but never stopping) around 1:20.  If I try to track to anywhere, Totem stops playing immediately.  VLC displays the total time as 0:0:31.  Tracking is better, but it always goes behind where I click and inevitably it stops playing after a number of moves.  MPlayer displays the correct total time and tracks perfectly within about the first 15 minutes.  If I try to track to anywhere outside that, it stops playing.

Also, nautilus did not generate a thumbnail for the file.  Is there anything I can do to make the players behave?  Or is there a more accessible format for ripping DVDs in full quality?

---

### Post by andrew.46 on 2010-06-02
Hi marshmallow,

> **marshmallow1304 said:**
>  MPlayer displays the correct total time and tracks perfectly within about the first 15 minutes.  If I try to track to anywhere outside that, it stops playing.

It might be worthwhile trying to play your file with the *-forceidx* option:

```
mplayer -forceidx my_file.vob
```

All the best,

Andrew

---

### Post by marshmallow1304 on 2010-06-02
While researching your suggestion, I found [this]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2004-December/050181.html") which lead me to do
```
mencoder -oac copy -ovc copy -forceidx -o output-file.vob input-file.vob
```

Now, I've got a file that plays perfectly in Totem with the proper total length.  VLC displays the proper total length and also tracks properly, but it refuses to play the video, citing
> VLC does not support the audio or video format "   ". Unfortunately there is no way for you to fix this.
At this point, it doesn't matter to me, as long as Totem plays it.  Also, a thumbnail is now generated.

Thank you.



[EDIT] The new file is also .5 GB smaller.  I'm not particularly concerned though.

[EDIT] I spoke too soon.  The new file skips backward at some points.  I'll do some more experimentation.
[EDIT] The problem is with the original.  Maybe there's something better than vobcopy.

---

### Post by andrew.46 on 2010-06-02
Hi marshmallow1304,

Partial success anyway :). A major shortcoming with MEncoder is that it is really only designed to work with the avi container, although a few other containers are *possible*. I am not sure if FFmpeg can rebuild an index in this way...

Andrew

---

### Post by marshmallow1304 on 2010-06-02
I wonder if there is a better tool than vobcopy to backup DVDs from the command line.  I used OGMRip on a different machine and it created an MKV that, though a bit smaller than the .vobs, appeared to be of equal quality and played properly with no issues.


[EDIT] Whoa.  I just saw your sig.  The movie I'm ripping is *The Matrix*.  Whoa.

---

### Post by andrew.46 on 2010-06-02
Hi marshmallow,

> **marshmallow1304 said:**
> Whoa.  I just saw your sig.  The movie I'm ripping is *The Matrix*.  Whoa.

I presume when you say 'Whoa' you are quoting Neo's infamous comment when he sees Morpheus jump from one skyscraper to another :). Another technique to try for DVD ripping is:

```
mplayer -v dvd://1 -dumpstream -dumpfile matrix.vob
```

which works well enough.

All the best,

Andrew

---

### Post by marshmallow1304 on 2010-06-02
Good.  :D  The mplayer dump gives me good playback in VLC, the only problem being that all times are wrong.  I'll try rebuilding the index as before.


Yep, it works really well.  I can't play the re-indexed video in VLC, but it's fine in Totem.  Now I'm having OCD about whether one of the two (mplayer dump plus mencoder with -idx to matrix.vob or OGMRip with no encoding to matrix.mkv) is better in terms of quality.

---

