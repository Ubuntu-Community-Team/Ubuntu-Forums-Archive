---
title: "480 x 272 pixels, MPEG-4 AVI or WMV9"
date: 2008-08-26
forum: Multimedia Software
---

### Post by SyCo123 on 2008-08-26
I'm new to converting videos but I need to convert movies to 480 x 272 pixels, MPEG-4 AVI or WMV9 for a media players GPS. Command line is fine but I've no idea where to begin. Any help is appreciated.

---

### Post by Creative2 on 2008-08-26
search for fuoco tools----------->[http://ubuntuforums.org/showthread.php?t=776412](http://ubuntuforums.org/showthread.php?t=776412)
or pytube or winff 
 (wmv9 is impossible to get in linux you can get only wmv2)

---

### Post by SyCo123 on 2008-08-26
Thanks creative2 I've installed everything via your link and it went well (Hardy/Mint in virtual box). Great docs so thanks for your hard work.

The video encoded to mpeg4 but the dimensions remained the same as the input video. Is there a way to reduce the size to the dimensions my player requires?

I'm guessing I'll need to edit this line in 
video>to MP4>Any to MP4 TaG low quality>
ffmpeg -i INPUT -r 25 -f mp4 -vcodec mpeg4 -ar 48000 -b 500k  -ab 128k -y OUTPUT 

But I've no idea to what.

---

### Post by Creative2 on 2008-08-26
what kind of player do you have? if you go in "portable device " there are many example for psp and others 

anyway you can try with this

ffmpeg -i INPUT -r 25 -s 480x272 -f mp4 -vcodec mpeg4 -ar 48000 -b 500k -ab 128k -y OUTPUT  

i am actually doing a button version of this converter :S  so maybe it will be added in next version (not so soon...)

---

### Post by SyCo123 on 2008-08-26
found it!!

Under 
Portable devices>PSP 

Sweet! Thanks again. Very painless and just what I needed. I hope it's as easy tom install on my laptop at home. :)

---

