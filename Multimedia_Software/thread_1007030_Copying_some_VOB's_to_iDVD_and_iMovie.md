---
title: "Copying some VOB's to iDVD and iMovie"
date: 2008-12-10
forum: Multimedia Software
---

### Post by DrSpirograph on 2008-12-10
I wanted to make a compilation DVD for my family to send home over Christmas of some various personal video's I've got.
I don't have a DVD burner, but I have access to a Mac with iMovie and iDVD - but I don't have admin privileges on it, so I can't install new software on it.

Some of the video's I want to use are on DVD (unencrypted) - which Apple (in their infinite wisdom) has decided is not a suitable format for importing into iDVD or iMovie.
So, how can I convert these files on my Ubuntu laptop, into a format that I can use with iDVD?

The closest to success I came was with ffmpeg converting to DV.
```
ffmpeg -i infile.vob -target dv -o outfile.dv
```
It would convert VOB's that I'd ripped, but I could only seem to do it one VOB at a time, and for a long DVD, the VOB is split into multiple files.
I thought that would be fine, but after I converted, I discovered the last few seconds of each VOB was missing, so it couldn't be put back together smoothly in iMovie.

Can anyone give me a straight forward answer on how to convert (preferably to a format other than DV since it takes up masses of space making it hard to manage).
I've tried googling, and found heaps of "try ffmpeg" or "try mencoder" or "try transcode", but when it comes to specific command line options, then details get hazy, and I haven't been able to figure out the correct combination.

Cheers.

---

### Post by sawyer11 on 2009-09-01
**VOB** is basically one of the core files found on DVD-Video discs and contains the actual movie data, also there are .vob HD Video besides DVD. In order to view stand-alone VOB files, you need to have a DVD player software that supports VOB playback, if you need to import VOB to iMovie, QuickTime, Adobe Premiere, etc, just convert it.Convert [VOB to MOV]("http://www.applemacvideo.com/howtoconvert/movmac/vob-to-mov-mac.html#119") for Mac OS X.

---

