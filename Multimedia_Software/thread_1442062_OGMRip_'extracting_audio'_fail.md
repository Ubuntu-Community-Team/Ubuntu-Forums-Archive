---
title: "OGMRip 'extracting audio' fail"
date: 2010-03-29
forum: Multimedia Software
---

### Post by helamsirrine on 2010-03-29
I have an acer aspire 1301 with dual athlon II's, and I am running 64 bit Karmic. I have been using OGMRip with some success for a while now, but recently it failed on me mid que. I was encoding firefly episodes for my brothers iPod when I found that the last episode on the disc had not finished encoding.

I tried it again and watched it carefully this time. in the middle of extracting the audio stream it hung. Eventually it timed out and started over. Then it progressed to 99% and suddenly failed. I was encoding from an ac-3 source to AAC audio in an MP4 package and I retried several times with Identical results. The faac process died suddenly and the encoding just stopped.

Since then I have removed and reinstalled OGMRip, libogmrip-aac, and faac, but when I tried to encode another dvd I ran into the same problem. Since this was not for the iPod I tried changing audio encoders. Using MP3 and ac3 copy the file still hung and failed in the middle of extracting the audio stream.

For thoroughness I am pasting in the log from my last attempt, though reading it has not given me any insight into the failure. Maybe I'll monitor active processes in a terminal and post the result, though I cant remember howto just now. Any help is appreciated. Thanks in advance.


```
ENCODING: Vampire Hunter D - Bloodlust


Profile: /apps/ogmrip/profiles/default-ps3
--------

version = 1.0
subp/forced = false
subp/charset = 0
subp/codec = srt
subp/spell_check = false
subp/newline = 1
audio/quality = 10
audio/srate = 0
audio/channels = 1
audio/normalize = false
audio/codec = aac
video/max_height = 1080
video/max_width = 1920
video/codec = x264
video/expand = false
video/can_crop = true
video/dering = false
video/qpel = false
video/denoise = true
video/turbo = false
video/trellis = true
video/scaler = 7
video/passes = 2
video/deblock = false
video/preset = 0
video/encoding = 1
video/quantizer = 2.000000
video/bitrate = 2500
container/format = mp4
container/ensure_sync = true
container/target_size = 700
container/fourcc = 0
container/target_number = 1
x264/global_header = true
x264/vbv_bufsize = 20000
x264/bframes = 3
x264/weight_b = true
x264/cabac = true
x264/aud = true
x264/me = 3
x264/level_idc = 41
x264/b_pyramid = false
x264/subq = 6
x264/vbv_maxrate = 20000
x264/dct8x8 = true
x264/mixed_refs = true
x264/frameref = 3


Analyzing video title 1
-----------------------

mplayer -nolirc -nosound -nocache -noconfig all -v -benchmark -vo null -vf pullup -dvdangle 1 -frames 500 -dvd-device /dev/sr0 dvd://1 

Telecine: true
Progressive: true


Encoding audio stream 01
------------------------

mplayer -nolirc -nocache -noframedrop -noconfig all -vc dummy -vo null -ao pcm:waveheader:file=/tmp/fifo.7JIX9U -channels 2 -aid 128 -dvd-device /dev/sr0 dvd://1 
faac -q 500 --mpeg-vers 4 -o /tmp/audio.LHIX9U /tmp/fifo.7JIX9U 

Setting video parameters
------------------------
Constant bitrate: 2500000 bps

mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf yadif=0,cropdetect -ss 1220 -frames 12 -dvd-device /dev/sr0 dvd://1 
mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf yadif=0,cropdetect -ss 2440 -frames 12 -dvd-device /dev/sr0 dvd://1 
mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf yadif=0,cropdetect -ss 3659 -frames 12 -dvd-device /dev/sr0 dvd://1 
mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf yadif=0,cropdetect -ss 4879 -frames 12 -dvd-device /dev/sr0 dvd://1 

Automatic cropping: 10,8 704x464

Automatic scaling: 720x400

TESTING: Vampire Hunter D - Bloodlust

mencoder -nocache -noslices -noconfig all -oac pcm -srate 8000 -af channels=1,lavcresample=8000 -aid 128 -sws 7 -zoom -frames 15 -vf pullup,softskip,crop=704:464:10:8,yadif=0,scale=720:400,hqdn3d=2:1:2,harddup -ofps 24000/1001 -dvdangle 1 -o /tmp/video.FSW69U -dvd-device /dev/sr0 -ovc x264 -x264encopts deblock=1,1:aq_strength=0.6:subq=10:direct_pred=auto:frameref=32:b_adapt=2:b_pyramid:weight_b:noglobal_header:8x8dct:mixed_refs:me=umh:merange=24:level_idc=51:cabac:partitions=all:trellis=2:bframes=6:psy-rd=0.40,0.00:crf=18:threads=2 dvd://1 
```

---

### Post by Deersindal on 2010-07-27
I know it's been a few months since you posted this, but did you ever find a resolution? I am having a similar problem right now.

---

