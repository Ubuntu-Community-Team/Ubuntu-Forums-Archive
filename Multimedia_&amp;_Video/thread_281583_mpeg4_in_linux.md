---
title: "mpeg4 in linux"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by einKI on 2006-10-21
Hi

i converted a movie to mpeg4 with ffmpeg. There was no errors given and the
conversion should be okay because if I replace -vcodec mpeg4 with -vcodec mpeg2 it works as it should.
(ffmpeg -deinterlace -i deinterlace_test.mpg -ab 128 -vcodec mpeg4 -b 4096 mpg4.mpg )

But when I trie to play the video in totem-xine i get a black screen and one the command line it prints
"bad sequence header"

vlc and ffplay also shows no video so it is no problem with totem apparently.

The sound works.
I have also installed all the gstreamer0.10-plugins* and the packages mentionend on the wiki page.

So how do I play mpeg4 files in linux?

by
Lukas

---

