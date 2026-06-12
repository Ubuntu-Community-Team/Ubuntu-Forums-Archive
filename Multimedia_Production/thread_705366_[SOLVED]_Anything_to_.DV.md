---
title: "[SOLVED] Anything to .DV"
date: 2008-02-23
forum: Multimedia Production
---

### Post by stooshbunutu on 2008-02-23
So I like the look and feel of Kino video editor but it only likes the use of .dv files. When it tries to import other file formats and convert in the process it does it really badly and the video never works properly.

So I was just wondering if there was a video converter that would change a normal* video format into a .dv file for use with Kino so that I can use its video editing. also transferring back from .dv to other normal* formats would be good but not as essential.

* by normal I mean anything realy as I already have WinFF which handles most file formats (unfortunately not .dv) eg. .flv .mov .wmv .ogg .avi .mpg .mpeg

Cheerz in advance

---

### Post by Creative2 on 2008-02-23
see fuoco tools, if you don't like try do this in a terminal 


NTSC DV (AMERICA)

ffmpeg -i INPUT -target ntsc-dv  OUTPUT.dv


PAL (EUROPE)  

ffmpeg -i INPUT -target pal-dv  OUTPUT.dv



for wmv  you can get some problem with that command line so this is my partial solution:


mencoder INPUT -ofps 30 -ovc lavc -oac mp3lame  -o OUTPUT.dv

you can find fuoco link on my signature

---

### Post by stooshbunutu on 2008-02-23
Cheers the script works great.

The problem is that each minute of .dv video takes up about 200MB

Would the same script work for converting to .avi files? I am going to give avidemux a proper trail.

Cheers again

---

### Post by FakeOutdoorsman on 2008-02-24
200 MB/min is normal since DV uses about 3 MB/sec. AVI is a container format which can contain many types of codecs like divx, mpeg-4, dv, xvid, etc.

---

### Post by Creative2 on 2008-02-24
dv is that .... a big big big file...of couse you can encode into avi
fuoco is maybe an universal converter so it can encode in every formats

---

### Post by stooshbunutu on 2008-02-24
Thanks all for your help

---

