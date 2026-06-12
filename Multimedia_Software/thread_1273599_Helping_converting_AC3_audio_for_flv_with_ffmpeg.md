---
title: "Helping converting AC3 audio for flv with ffmpeg"
date: 2009-09-23
forum: Multimedia Software
---

### Post by tstack77 on 2009-09-23
I have jinzora set up to transcode videos on my server to flash/mp3, and I'm having issues with trying to convert the audio portions. So far I've been able to stream most audio types but cannot get AC3 6 channel audio to work/convert to 2 channel mp3.

Below is the error that gets thrown out. Any ideas to what I can do to get this up and running?

```
FFmpeg version SVN-r16172, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac 
--enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 3 / 52. 6. 3
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 16 2008 14:41:39, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (959/40)
Input #0, avi, from '/media/Video/sample.avi':
  Duration: 02:07:03.44, start: 0.000000, bitrate: 1539 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x272 [PAR 1:1 DAR 40:17], 23.98 tb(r)
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, flv, to 'pipe:':
    Stream #0.0: Video: flv, yuv420p, 640x272 [PAR 1:1 DAR 40:17], q=2-31, 1280 kb/s, 20.00 tb(c)
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 5.1, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height


```

---

### Post by FakeOutdoorsman on 2009-09-23
What is your FFmpeg command?

---

### Post by comgen on 2009-12-20
Give this a try:

# AC3 audio AVI to FLV 16:9
ffmpeg -i name-OF-src-VID-here.avi -vcodec flv -f flv -r 29.97 -s 320x180 -aspect 16:9 -b 500kb -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -ac 1 -ar 22050 -ab 64kb NAME-of-OUT-put-VID-here.flv

Tweak Notes:

Fullscreen change 16.9 to 4:3
# I find the following works well with mythtv 40" TV playback
Change: -s 320x180 to -s 320x240 
# For media center, local media player playback 500k is fine
# For Webserver flashplayer.
# Depends on bandwidth
Change: -b 500kb to -b 300kb
# Audio 
Adjust: -ab 64kb to taste ( -ab 128kb )
# For flash I would leave this as is
Adjust: -ar 22050 to taste ( -ar 48000 )

# Working examples based on * MY * prefs + 40" TV screen and Mythtv 

# AC3 to flash
ffmpeg -i name-OF-src-VID-here.avi -vcodec flv -f flv -r 29.97 -s 320x240 -aspect 16:9 -b 500kb -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -ac 1 -ar 22050 -ab 64kb NAME-of-OUT-put-VID-here.flv

# Xvid - MP3 - standard avi to flash
ffmpeg -i video-src-NAME-here.avi -s 320x240 -aspect 16:9 -b 500k -acodec libmp3lame -ab 64k -ar 22050 -f flv OUTput-vid-name-here.flv

#### START EXAMPLE SCRIPT ####

#!/bin/bash
#
# Batch process avi to WS flv 
# updated 12-20-09 
# 
# NAME: dir-vid-to-flash.sh
# chmod +x or chmod 775 ( make exec )
# Create a working folder for vid processing
# Place ALL video-src.avi and dir-vid-to-flash.sh into the folder
# Drop to term in the folder, TYPE: ./dir-vid-to-flash.sh
##
## Note: multiple configs, add or remove comment ( # ) 
## to enable or disable
## do this for " for f in " and the " ffmpeg " command
## Default: avi with ac3 audio to flv

for f in *.avi;

#for f in *.flv;
#for f in *.mp4;
#for f in *.mp3;

do
echo "Processing $f"

## -ar 44100 22050 48000
## -aspect WS = 16:9 , TV = 4:3
## -b 500k , 300k , 1000k , 256k
## -ab 64k , 128k , 192k , 448k 

#### AC3 audio avi to flash

ffmpeg -i "$f" -vcodec flv -f flv -r 29.97 -s 320x240 -aspect 16:9 -b 500kb -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -ac 1 -ar 22050 -ab 64kb "${f%.avi}.flv" 

#### Standard avi ( non AC3 )

#ffmpeg -i "$f" -s 320x240 -aspect 16:9 -b 500k -acodec libmp3lame -ab 64k -ar 22050 -f flv "${f%.avi}.flv"

#### mp4 to flv

#ffmpeg -i "$f" -s 320x240 -aspect 16:9 -b 500k -acodec libmp3lame -ab 64k -ar 22050 -f flv "${f%.mp4}.flv"

#### MP3 - MISU ####

## audio books, podcast, Low-q
#ffmpeg -i "$f" -b 56k -ar 22050 "${f%.mp3}-O.mp3"

## general music
#ffmpeg -i "$f" -ab 192k "${f%.mp3}-O.mp3"

#### HD HQ HI-RES LARGE - 2 PASS AVI to FLV
## NOTE: tweaking might be required

#ffmpeg -i "$f" -ab 64k -ar 22050 -vcodec flv -b 700k -s 320x240 -bt 100k -qmin 1 -qmax 15 -g 160 -cmp 3 -subcmp 3 -mbd 2 -flags +aic+cbp+mv0+mv4+trell -pass 1 "${f%.avi}.flv"

#ffmpeg -y -i "$f" -ab 64k -ar 22050 -vcodec flv -b 700k -s 320x240 -bt 100k -qmin 1 -qmax 15 -g 160 -cmp 3 -subcmp 3 -mbd 2 -flags +aic+cbp+mv0+mv4+trell -pass 2 "${f%.avi}.flv"

#### END EXAMPLE SCRIPT ####

---

