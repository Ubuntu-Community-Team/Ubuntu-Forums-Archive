---
title: "mkv+subtitle -&gt; mp4"
date: 2010-01-23
forum: Multimedia Software
---

### Post by hasch on 2010-01-23
Hi! I was wondering if there is any option to convert my mkv file with the included subtitles into a mp4? The mkv-info says
```
+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 177669372
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4027)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.6 + libmatroska v0.8.0
| + Writing application: mkvmerge v1.6.5 ('Watcher Of The Skies') built on Mar 17 2006 17:24:57
| + Duration: 1193.280s (00:19:53.280)
| + Date: Tue Jul 24 19:24:19 2007 UTC
| + Title: DBZ Uncut (Released by Phantom1)
| + Segment UID: 0xa9 0xbe 0xf4 0x88 0xbd 0x48 0x08 0x17 0x8a 0xe0 0x21 0x99 0xae 0x5f 0x7e 0x42
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 3134581944
|  + Track type: video
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 1
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Codec decode all: 1
|  + CodecPrivate, length 41
|  + Default duration: 40.003ms (24.998 fps for a video track)
|  + Language: jpn
|  + Video track
|   + Pixel width: 720
|   + Pixel height: 480
|   + Interlaced: 0
|   + Display width: 864
|   + Display height: 480
| + A track
|  + Track number: 2
|  + Track UID: 2383120031
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_MPEG/L3
|  + Codec decode all: 1
|  + Default duration: 24.000ms (41.667 fps for a video track)
|  + Language: ger
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 1
| + A track
|  + Track number: 3
|  + Track UID: 849905321
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_MPEG/L3
|  + Codec decode all: 1
|  + Default duration: 24.000ms (41.667 fps for a video track)
|  + Language: eng
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 2
| + A track
|  + Track number: 4
|  + Track UID: 2957482636
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_MPEG/L3
|  + Codec decode all: 1
|  + Default duration: 24.000ms (41.667 fps for a video track)
|  + Language: jpn
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 1
| + A track
|  + Track number: 5
|  + Track UID: 1981533361
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/UTF8
|  + Codec decode all: 1
|  + Language: ger
| + A track
|  + Track number: 6
|  + Track UID: 2474917511
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/UTF8
|  + Codec decode all: 1
|  + Language: eng
|+ EbmlVoid (size: 1024)
|+ Cluster
``` First thing I did was to extract the necessary tracks
```
$ mkvextract tracks planet.mkv 1:video.h264 2:audio.ac3 5:subtitle.srt
```Following I "hexedited" the video (number 33 to 29) saved and turned up converting the audio.ac3 to aac
```
$ mkfifo audiodump.wav
$ neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -ao pcm:fast
```After that I tried to add all the tracks to the new mp4.
```
$ MP4Box -add video.h264 -add audio.m4a -add subtitle.srt try1.mp4
AVC-H264 import - frame size 720 x 480 at 25.000 FPS
Import results: 29832 samples - Slices: 402 I 13578 P 15852 B - 0 SEI - 337 IDR
    Stream uses B-slice references - max frame delay 2
IsoMedia import - track ID 1 - HE-AAC (SR 24000 - SBR-SR 48000 - 1 channels)
Timed Text (SRT) import - text track 720 x 480, font Serif (size 18)
Saving to try1.mp4: 0.500 secs Interleaving
``` Sadly to say the subtitle isn't in the video! :( Could someone help me out? Would really appreciate it!

Greets Hasch

---

### Post by lovinglinux on 2010-01-23
I guess MP4Box does not hardcode the subs. That never worked for me. The best results I get is by hardcoding the subs with mencoder.

```
mencoder source_video.avi -sub source_subtitles.ssa -a\s\s -a\s\s-color FFFF0000 &#8722;a\s\s&#8722;font&#8722;scale 3 -o output_video.mp4 -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=libx264:vbitrate=1500
```

---

### Post by hasch on 2010-01-23
thanks for the bash-command! :) Is that the only way to fix this? I don't really have to cpu-power to encode all the episodes in conceivable time... :( So still in hope to get something - less new encoding! ;)

Greets Hasch

---

### Post by lovinglinux on 2010-01-23
> **hasch said:**
> thanks for the bash-command! :) Is that the only way to fix this? I don't really have to cpu-power to encode all the episodes in conceivable time... :( So still in hope to get something - less new encoding! ;)

Greets Hasch

Where do you want to play the files, XBOX?

---

### Post by hasch on 2010-01-24
close - but in this case it's for the ps3! ;)

greets

---

### Post by lovinglinux on 2010-01-24
> **hasch said:**
> close - but in this case it's for the ps3! ;)

greets

Then, if you don't want to re-encode, I'm afraid MP4Box is the way to go. Unfortunately, I can't help you any further, but I'm sure someone will step in with a solution.

---

