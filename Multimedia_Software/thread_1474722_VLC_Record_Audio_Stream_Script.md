---
title: "VLC Record Audio Stream Script"
date: 2010-05-06
forum: Multimedia Software
---

### Post by rowbird on 2010-05-06
Hi all,

 I was wondering is somebody could look at this simple script that I am working on. I cannot get it to output to my home directory. I noticed the message "bad input or output format" in the VLC verbose terminal, but i don't know how to fix it. Any help would be greatly appreciated. Thanks in advance.

---

### Post by mc4man on 2010-05-06
Well for starters try changing to acodec=mp3 (not mpga

Also you need to use /home/<your user name> for OUTFILE
Ex. mine is 
/home/doug

(overall the stream is *very* low quality - don't know how well it's going to sound - you may be better off just coping it as is - ( not ab=96.

---

### Post by rowbird on 2010-05-06
Thanks for the reply, I tried the changes , but still no output file in my home folder. Here is the updated script and terminal output.

---

### Post by mc4man on 2010-05-06
Well for what it does works fine here.

Using basically what you posted (because I had to hand type and I can't type to well removed a few lines.

The stream is as mentioned low quality (24 Kbps, 8000 Hz) so your ab will max at 64 anyway. (or remove the ab= altogether -  now see you did that.

```
#!/bin/sh
NOW=$(date +%F_%k-%M)
INSTREAM=http://radio.ghanaweb.com/radio.asx?ID=2
OUTFILE=/home/doug/$NOW.mp3
echo ...
echo ...Recording Ghanaweb Waves internet to
echo      $OUTFILE
echo ...
/usr/bin/vlc  -v $INSTREAM ':sout=#transcode{acodec=mp3,channels=2}:duplicate{dst=display,dst=std{access=file,mux=raw,dst="'$OUTFILE'"}}'


```

> doug@doug-desktop:~$ trans1
...
...Recording Ghanaweb Waves internet to
/home/doug/2010-05-06_18-04.mp3
...
VLC media player 1.0.6 Goldeneye
[0x9da8b10] main demux warning: no access_demux module matching "file" could be loaded
[0x9f36298] mux_dummy mux: Open
[0x9e39350] ts demux error: cannot peek
[0x9f30e48] mux_dummy mux: Open
[0x9f67ee8] access_http access warning: ICY metaint=8192
[0x9f67ee8] access_http access: Raw-audio server found, mp3 demuxer selected
[0x9fdd020] scaletempo audio filter warning: bad input or output format
[0x9fdd020] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
<blinking cursor> as stream is saved


 as far as this particular stream you could capture other ways - no need to script vlc - you could even just push the record button on vlc

---

