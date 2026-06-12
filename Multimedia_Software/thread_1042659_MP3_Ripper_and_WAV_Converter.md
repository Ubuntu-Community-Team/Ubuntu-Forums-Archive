---
title: "MP3 Ripper and WAV Converter"
date: 2009-01-17
forum: Multimedia Software
---

### Post by Killtodie on 2009-01-17
There a good MP3 Ripper and wave converter in ubutnu? Like LAME or something but maybe with a gui

What I really need it to do is be able to rip an entire music CD of multiple tracks into a single track.

---

### Post by logos34 on 2009-01-18
**K3b** can do it:

>Tools>Rip Audio CD>[select all]>Start Ripping>Options: **'Create single file'**

Or **abcde** (CLI only):

sudo apt-get install abcde 

> abcde -1 -o mp3

Or again from the terminal:

sudo apt-get install libcdio-utils

> cd-paranoia "1-" -- | lame -V 2 - album.mp3

The above will rip entire CD from track 1 to end and pipe it to lame to encode into a single file 'album.mp3' @ VBR quality 2 (~192 kbps)

for all the above you'll need the lame pkg/plugins of course

---

