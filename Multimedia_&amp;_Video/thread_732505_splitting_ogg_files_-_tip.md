---
title: "splitting ogg files - tip"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by logos34 on 2008-03-23
I just dowloaded the newest **vorbis-tools (1.2.0) **tar.gz source, and I noticed it includes a command-line ogg file splitter called **vcut** (didn't know this before), but you have to compile it separately from the rest.

Simply do:

> $ cd vorbis-tools-1.2.0/vcut
$ make

The resulting file should be executable by default.  Copy it to /usr/bin or /usr/local/bin.

> Usage: 
$ vcut -h
vcut infile.ogg outfile1.ogg outfile2.ogg [cutpoint | +cutpoint] 

(where '+cutpoint' = seconds)

i.e. 
> $ vcut infile.ogg outfile1.ogg outfile2.ogg **+12**
(cuts track 12 seconds from beginning)

I use mp3directcut on wine for the most part, but this will come in handy for trimming down some of the  radio talk show ogg downloads I've accumulated

---

