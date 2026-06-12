---
title: "Split video files (.mp4, .avi, .wmv, .mkv)"
date: 2013-09-01
forum: Multimedia Software
---

### Post by marfin2 on 2013-09-01
Hi,

I try to split videos on Ubuntu 12.10 and I found MKVmerge for splitting matroska (.mkv) and Avidemux for splitting avi files.

Could you tell me what software (or commands) I can use to split .mp4 and .wmv files please ?

Thanks for your help.

---

### Post by GwL3eNC on 2013-09-01
Hello,

you can try ffmpeg for the mp4 files

ffmpeg -acodec copy -vcodec copy -ss START -t LENGTH -i ORIGINALFILE.mp4 OUTFILE.mp4

found it in less then a minute google search [http://askubuntu.com/questions/35605/splitting-an-mp4-file](http://askubuntu.com/questions/35605/splitting-an-mp4-file)

Avidemux can handle wmv since version 2.3.0 if you have all codecs installed.

sudo apt-get install non-free-codecs

in sum two minutes goolge, why can't you do that.

---

### Post by marfin2 on 2013-09-02
Thanks for your help.

For FFMpeg, that I use, I consider that it's not a really split, but a conversion that allows multiple small files in output. The problem is that conversion is much longer than a split.

I didn't know for wmv and avidemux, thanks !

---

### Post by rai_shu2 on 2013-09-02
I don't know about wmv. I suppose you could just use VirtualDub in Wine/Windows. Avidemux should work with mp4, surely?

---

### Post by shantiq on 2013-09-02
duplicate.

---

### Post by shantiq on 2013-09-02
hi marfin

you can use ffmpeg or mencoder to split video file in multiple sections


use same input file add "**&&**"   between cuts and do as many sections as you need to
First time entry is where you start from.   Second time entry the **duration** you require


> ffmpeg -i INPUT.mp4 -ss 00:35:54 -t 00:04:12 -vcodec copy -acodec copy OUTPUT1.mp4 && ffmpeg -i INPUT -ss 01:14:14 -t 00:14:10 -vcodec copy -acodec copy OUTPUT2.mp4  && etc...


or

> mencoder  -ss 01:00:00  -endpos 00:05:56 -oac copy -ovc copy INPUT.mp4 -o OUTPUT1.mp4 && mencoder  -ss 01:20:00  -endpos 00:05:56 -oac copy -ovc copy INPUT.mp4 -o OUTPUT2.mp4 && etc...



iN MY PERSONAL experience [mencoder]("http://www.misterhowto.com/index.php?category=Computers&subcategory=Video&article=trim_or_split_with_mencoder") is more stable for this task

---

### Post by marfin2 on 2013-09-02
Thanks a lot everyone.
And mea culpa for my for my wrong remark on FFmpeg : if we use "-vcodec copy -acodec copy" and we have the same format in the input and output, FFmpeg split correctly the file (and don't convert as I thought).
rai_shu2> I can't use VirtualDub beacause I need use tools with command lines, but thanks for the idea.

---

### Post by marfin2 on 2013-09-06
Just one question : why when I use FFmpeg to convert (not to split), even if I put the bitrate video and audio, the bitrate video (but not the bitrate audio) is out from metadata ?

---

