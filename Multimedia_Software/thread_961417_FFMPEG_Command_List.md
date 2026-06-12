---
title: "FFMPEG Command List"
date: 2008-10-28
forum: Multimedia Software
---

### Post by tufcamman on 2008-10-28
Hey everyone, I'm starting this post in hopes of starting a list of commands people use with ffmpeg and how they work.  I know there are a lot of complicated settings with ffmpeg and I'm just trying to compile everyone's experience into one place.  So, anyway, list the different commands you use, what they do, and how they have worked out for you.  Heres mine.

Convert input files to high quality x264 files

```
ffmpeg -i INPUT -an -pass 1 -vcodec libx264 -b 624k -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me_method dia -subq 1 -trellis 0 -refs 1 -bf 16 -b_strategy 1 -coder 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 300k -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -threads 3 OUTPUT.mp4

ffmpeg -i INPUT -acodec libfaac -ab 128k -pass 2 -vcodec libx264 -b 624k -flags +loop -cmp +chroma -partitions +parti8x8+parti4x4+partp8x8+partp4x4+partb8x8 -flags2 +dct8x8+wpred+bpyramid+mixed_refs -me_method umh -subq 7 -trellis 1 -refs 6 -bf 16 -directpred 3 -b_strategy 1 -coder 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 300k -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -threads 3 OUTPUT.mp4
```

I got most of it from [http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/)

It seems to work well, audio/video isn't perfectly aligned, and I can't write to /dev/null.  Not sure why.  So, anything else anybody's got would be great.  Thanks!

---

### Post by FakeOutdoorsman on 2008-10-28
The easiest and most convient way to encode with ffmpeg using libx264 is by using the new [FFmpeg libx264 presets]("http://rob.opendot.cl/index.php/2008/09/17/ffmpeg-libx264-presets/").  The presets were written by the developers, have excellent option settings, and will always be up to date.  More presets are planned soon for H.264 profiles/levels and iPods.  You will need to use a recent version of ffmpeg because the versions of ffmpeg in Medibuntu and the universe repository are very old.  Here's my guide:
[URL="http://ubuntuforums.org/showthread.php?t=786095"]
HOWTO: Compile the latest ffmpeg and x264 from source[/URL]
Preset usage is explained in the above link too.

> It seems to work well, audio/video isn't perfectly aligned, and I can't write to /dev/null.  Not sure why.
I haven't had any synch issues before, but if you want to write to /dev/null, then you need to change your first pass line to (changes in blue):
```
ffmpeg -i INPUT -an -pass 1 -vcodec libx264 -b 624k -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me_method dia -subq 1 -trellis 0 -refs 1 -bf 16 -b_strategy 1 -coder 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 300k -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -threads 3 [COLOR="Blue"]-f mp4 /dev/null[/COLOR]
```

---

### Post by tufcamman on 2008-10-29
Hey, thanks for the very useful info!  I found out though that the presets on his blog are no longer valid and don't work, now they're keeping up all the presets in the trunk.  So that's where I had to go to get them.

---

