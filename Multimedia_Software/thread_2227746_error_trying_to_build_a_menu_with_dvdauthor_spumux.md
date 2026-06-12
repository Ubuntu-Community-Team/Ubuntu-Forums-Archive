---
title: "error trying to build a menu with dvdauthor spumux 0.7.0"
date: 2014-06-03
forum: Multimedia Software
---

### Post by George Heine on 2014-06-03
Trying to create a simple DVD menu with:
 ```
spumux "menu_buttons.xml" < "menu.mpg" > "menu2.mpg"
```

Output and information on the input listed below
What does the error mean?
Appreciate any clues, hints, references, etc.
Thank you!
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Output from spumux:
```
DVDAuthor::spumux, version 0.7.0.
Build options: gnugetopt imagemagick iconv freetype fribidi fontconfig
Send bug reports to <dvdauthor-users@lists.sourceforge.net>

INFO: default video format is NTSC
STAT: 0:00:00.000
INFO: Picture highlight_buttons.gif had 2 colors
INFO: Picture select_buttons.gif had 2 colors
INFO: Constructing blank img
INFO: Autodetect 0 = 178x280-191x294
INFO: Autodetect 1 = 178x310-191x324
INFO: Autodetect 2 = 178x342-191x356
INFO: Autodetect 3 = 178x372-191x386
INFO: Autodetect 4 = 178x404-191x418
INFO: Pickbuttongroups, success with 1 groups, useimg=1
WARN: Incorrect pack header
INFO: Skipped 53234 bytes of garbage
...
 (above line repeated about 50 more times, with varying amounts of "garbage")
...
INFO: 0 subtitles added, 0 subtitles skipped, stream: 32, offset: -0.00
```
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
file "menu_buttons.xml":

```
<subpictures format="ntsc">
  <stream>
  <spu force="yes" start="00:00:00.00"
       transparent="0000FF"
       highlight="highlight_buttons.gif"
       select="select_buttons.gif"
       autooutline="infer">
  </spu>
  </stream>
</subpictures>
```
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
"menu.mpg" is a 4-second silent video with a background image and
text describing the menu choices.  Did not include due to size,
but here is the tail from "ffprobe menu.mpg":

```
Input #0, mpeg, from 'menu.mpg':
  Duration: 00:00:03.95, start: 0.523344, bitrate: 1075 kb/s
    Stream #0:0[0x1e0]: Video: mpeg1video, yuv420p(tv), 720x480 [SAR  200:219 DAR 100:73], 104857 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 29.97  tbc
    Stream #0:1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16p, 128 kb/s
```
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
The files "select_buttons.gif" and "highlight_buttons.gif"
each contain a column of solid circles with a transparent
background.  The circles serve as buttons aligned with
text in the input file "menu.mpg."  The files were created
with the script:

```
convert -size 720x480 xc:blue -fill $FILLCOLOR \
-draw 'circle 184,286 190,286' \
-draw 'circle 184,317 190,317' \
-draw 'circle 184,348 190,348' \
-draw 'circle 184,379 190,379' \
-draw 'circle 184,410 190,410' \
-colors 2 \
tmp.gif
convert -transparent blue tmp.gif $FILENAME
```

---

### Post by George Heine on 2014-06-05
Posted this message to the dvdauthor forums; a reply there suggested that the input video "menu.mpg" might not be in a suitable format.

Recreated menu.mpg from an old static image "menu_outline.png":

```
ffmpeg -loop 1 -i menu_outline.png -vcodec png -t 4 bg.mkv
ffmpeg -f s16le -ar 48000 -ac 2-i /dev/zero -ab 224k -t 4 -acodec ac3 -y tmp.ac3
ffmpeg -y -i bg.mkv -i tmp.ac3 -target ntsc-dvd -aspect 16:9 menu.mpg

```

Output from ffprobe is now:

```
Stream #0:0[0x1bf]: Data: dvd_nav_packet
Stream #0:1[0x1e0]: Video: mpeg2video (Main), yuv420p(tv), 720x480 [SAR  32:27 DAR 16:9], max. 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94  tbc
Stream #0:2[0x80]: Audio: ac3, 48000 Hz, stereo, fltp, 448 kb/s
Unsupported codec with id 1145979222 for input stream 
```

The command```

   spumux "menu_buttons.xml" < "menu.mpg" > "menu2.mpg"
```
now work withouts errors (and I was able to successfully attach the menu to a dvd).

Questions:

Spumux needs an input video with a dvd_nav_packet stream to create a menu?

The ffmpeg option "-target [ntsc|pal]-dvd" creates an dvd_nav_packet stream, even though it is "unsupported"?

---

