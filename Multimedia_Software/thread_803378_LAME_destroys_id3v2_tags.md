---
title: "LAME destroys id3v2 tags"
date: 2008-05-22
forum: Multimedia Software
---

### Post by casperlingus on 2008-05-22
I wrote a python script to convert part of my entire music library from 256 kbps to 128 kbps, using lame.  I didn't realize until it was done that this error was showing up on every lame operation:

```
ID3v2 found. Be aware that the ID3 tag is currently lost when transcoding.
LAME 3.97 32bits (http://www.mp3dev.org/)

```

I wouldn't be opposed to re-downsampling all of them, it only took 1.5 days (and I'm not in a hurry), but I'm not really sure if I should use a different program, or if there's a good option for lame.  I looked at the man pages and found some id3 tag options, but none of them seem to *read the original id3v2 tags* it'll only write id3v2 tags if requested.  I still get the same error.

Any recommendations?

---

### Post by Xiong Chiamiov on 2008-05-22
There's built-in batch mp3 processing in audacity.  File -> Apply Chain and select a folder.  It will keep the tags, which makes it quite nifty.  However, test first, because I've been having a problem with it making my tracks so they appear twice as long as they actually are in all my media players.  I don't know if it's just a problem with me (I screw with things all the time), but it's always a good idea to test something out before running it on all your files.

---

