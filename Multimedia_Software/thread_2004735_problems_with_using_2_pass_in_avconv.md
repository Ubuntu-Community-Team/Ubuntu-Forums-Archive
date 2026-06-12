---
title: "problems with using 2 pass in avconv"
date: 2012-06-16
forum: Multimedia Software
---

### Post by Kuroc on 2012-06-16
I ripped a title off a dvd as a vob.
Now I'm trying to use the 2 pass method to encode it to shrink the file size.
But when ever I use a preset while using 2 pass I keep getting errors.
Here is all the information about it:


I'm using ubuntu 12.04
I using avconv version 0.8.1-4:0.8.1

The command I'm using is:
pass 1
avconv -i gtest.vob -c:v libx264 -pass 1 -pre anime -b:v 620K -threads 0 -filter:v yadif=1 -an -f mp4 -y /dev/null
pass 2
&& avconv -i gtest.vob -c:v libx264 -pass 2 -pre anime -b:v 620K -threads 0 -filter:v yadif=1 -c:a ac3 -b:a 224k -map 0:0 -map 0:1 output/gep1.mkv

The contents of anime.avpreset:

cmp=+chroma
weightp=2
coder=1
partitions=+parti8x8+parti4x4+partp8x8+partp4x4+partb8x8
me_method=umh
me_range=16
keyint_min=25
refs=16
trellis=2
flags2=+bpyramid+mixed_refs+wpred+dct8x8+fastpskip
qcomp=0.6
qmin=10
qmax=51
rc_lookahead=60
b-pyramid=2
bf=5
b_strategy=2
subq=9 

I keep getting errors on the 2nd pass it says:
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
and
Option weightp not found.
But if I remove weightp from the preset it just says another option is not found.

So what am I doing wrong?

---

### Post by FakeOutdoorsman on 2012-06-16
Where did you get this preset? Unfortunately you can't just find a random preset from the web and expect it to work due to major syntax changes between versions. Preset usage has changed. File based libx264 presets have been depreciated, and x264 presets (also "-profile" and "-tune") are now accessed directly. So instead of "-pre anime" you can use "-preset veryslow -tune animation". See available profiles, profiles, and tunes with *x264 --fullhelp*.

---

