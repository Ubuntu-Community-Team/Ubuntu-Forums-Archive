---
title: "Normalize a folder of music without using RG"
date: 2013-08-07
forum: Multimedia Software
---

### Post by Elastic_Potential on 2013-08-07
Greetings,

I was wondering if it'd be possible to normalize entire folders (ie, for an album) with music files without using ReplayGain (please don't suggest using RG tags).  I'm aware that Audacity does this for single songs, but I'd like to apply a -1dB gain to a series of albums, so I'd rather not do this one song at a time.

So, are there any programs that will normalize a constant gain to a series of songs all at once?

Any help be appreciated.
Thanks.

---

### Post by Elastic_Potential on 2013-08-07
Also, I noticed that mp3gain's -g <i> switch will apply a constant gain.  But, is there any way to do this to a folder of mp3 files?

---

### Post by evilsoup on 2013-08-08
You can just put it in a for loop.

```
for f in ./*.mp3; do mp3gain <options> "$f"; done
```

I've never used mp3gain, so I don't know what options would be correct. You can also get recursiveness --  the following will work on every .mp3 in the current directory and in all subdirectories (maybe useful if you want to do your whole ~/Music):

```
shopt -s globstar
for f in ./**/*.mp3; do mp3gain <options> "$f"; done
```

---

