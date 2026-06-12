---
title: "avconv can't copy subtitles with -ss"
date: 2013-02-24
forum: Multimedia Software
---

### Post by MisterPi on 2013-02-24
Has anyone seen this?  I'm trying to use avconv to rearrange streams in vob files.  I have a vob with 1 video, 2 audio and 2 subtitle streams (streams 0, 1-2, and 3-4, respectively).  If I do

avconv -i foo.vob -map 0:0 -map 0:1 -map 0:3 -c: copy -t 180 test.vob

I get a 3-minute vob with one video, audio, and subtitle stream, as I can confirm by running avconv on test.vob and seeing it identify 3 streams.

If I precede the -t switch in the cmd line above with '-ss 10' then the resulting vob does not have a subtitle stream, according to avconv.  However, it will work for some smaller skip values, like '-ss 1'.

For now this isn't a big deal; I'm just making fragments to experiment quickly.  Later it might be useful for extracting pieces out of VOB's.

---

