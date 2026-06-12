---
title: "extract audio [6 channels] from Bluray ?"
date: 2012-11-14
forum: Multimedia Software
---

### Post by shantiq on 2012-11-14
this is the file i want to extract the audio 2 and keep all its specs 

[FULL file plays perfect under SMplayer]


how can i do that with and/or ffmpeg or mencoder


so far i have tried  with no success
> ffmpeg -i 00000.m2ts -vn -acodec copy -y  'Rattle Conducts Tchaikovsky, Stravinsky, Rachmaninov'.pcm


extension wav   did not work either


what should i write in as an extension and should I do more to audio codec than copy

thanx for all useful input 




> mediainfo 00000.m2ts
General
ID                                       : 0 (0x0)
Complete name                            : 00000.m2ts
Format                                   : BDAV
Format/Info                              : Blu-ray Video
File size                                : 17.7 GiB
Duration                                 : 1h 43mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 24.6 Mbps
Maximum Overall bit rate                 : 48.0 Mbps

Video
ID                                       : 4113 (0x1011)
Menu ID                                  : 1 (0x1)
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 4 frames
Codec ID                                 : 27
Duration                                 : 1h 43mn
Bit rate mode                            : Variable
Bit rate                                 : 17.4 Mbps
Maximum bit rate                         : 35.0 Mbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Standard                                 : NTSC
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : MBAFF
Bits/(Pixel*Frame)                       : 0.281
Stream size                              : 12.6 GiB (71%)
Color primaries                          : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics                 : BT.709-5, BT.1361
Matrix coefficients                      : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio #1
ID                                       : 4352 (0x1100)
Menu ID                                  : 1 (0x1)
Format                                   : PCM
Format settings, Endianness              : Big
Format settings, Sign                    : Signed
Muxing mode                              : Blu-ray
Codec ID                                 : 128
Duration                                 : 1h 43mn
Bit rate mode                            : Constant
Bit rate                                 : 1 536 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Stream size                              : 1.11 GiB (6%)

Audio #2
ID                                       : 4353 (0x1101)
Menu ID                                  : 1 (0x1)
Format                                   : PCM
Format settings, Endianness              : Big
Format settings, Sign                    : Signed
Muxing mode                              : Blu-ray
Codec ID                                 : 128
Duration                                 : 1h 43mn
Bit rate mode                            : Constant
Bit rate                                 : 4 608 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Stream size                              : 3.33 GiB (19%)


---

### Post by evilsoup on 2012-11-14
First of all, I'd try it with a simpler filename, one without spaces or punctuation, like 'output.wav'or something. You can rename it later.

If you just want that one audio track, you should use the -map option

```
ffmpeg -i 00000.m2ts -map 0:2 -c:a copy output.wav
```

Should do it... if it doesn't, please post the ffmpeg output.

Also, you should consider using a lossless codec (you *could* convert to something like MP3, but a lot of people prefer lossless for classical music, especially if you're listening over speakers). It'll save you space over using raw PCM audio, without any loss in quality. FLAC is the standard linux recommendation for that, but I'm not sure if it supports surround-sound.

```
ffmpeg  -i 00000.m2ts -map 0:2 -c:a flac output.ogg
```

Also, if you don't have a surround-sound setup, you won't benefit from using the second audio track.

---

### Post by shantiq on 2012-11-14
ok thanx    what you have given me here is more of the same with different syntax   [ffmpeg picks the highest audio by default anyway [it seems]so no need for mapping]   my question is really about extension and acodec choices


it gave this

> Input #0, mpegts, from '00000.m2ts':
  Duration: 01:43:20.65, start: 36562.966644, bitrate: 24575 kb/s
  Program 1 
    Stream #0:0[0x1011]: Video: h264 (High) (HDMV / 0x564D4448), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0:1[0x1100]: Audio: pcm_bluray (HDMV / 0x564D4448), 48000 Hz, stereo, s16, 1536 kb/s
    Stream #0:2[0x1101]: Audio: pcm_bluray (HDMV / 0x564D4448), 48000 Hz, 5.1(side), s16, 4608 kb/s
[COLOR="Red"][wav @ 0x23a8700] NONE codec not supported in WAVE format[/COLOR]
Output #0, wav, to 'Rattle Conducts Tchaikovsky, Stravinsky, Rachmaninov.wav':
  Metadata:
    encoder         : Lavf54.25.105
    Stream #0:0: Audio: pcm_bluray (HDMV / 0x564D4448), 48000 Hz, 5.1(side), 4608 kb/s
Stream mapping:
  Stream #0:2 -> #0:0 (copy)
[COLOR="Red"]Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted[/COLOR]



same as i had before
:KS


now have also tried ffmlp  fflpcm  dvdpcm   they may only decode and not encode

---

### Post by evilsoup on 2012-11-14
> ffmpeg picks the highest audio by default anyway so no need for mapping

Oh yeah, so it does.

Hmm... maybe try .mkv? Or .avi.

---

### Post by shantiq on 2012-11-14
ok cracked it   [ hope this will help others in the same boat]   -ac 6 was needed here

> ffmpeg -i 00000.m2ts [COLOR="DarkRed"]-ac 6[/COLOR]  'Rattle Conducts Tchaikovsky, Stravinsky, Rachmaninov'.wav

also works but compressed

> ffmpeg -i 00000.m2ts [COLOR="DarkRed"]-ac 6[/COLOR]  'Rattle Conducts Tchaikovsky, Stravinsky, Rachmaninov'.flac



gives


> Input #0, mpegts, from '00000.m2ts':
  Duration: 01:43:20.65, start: 36562.966644, bitrate: 24575 kb/s
  Program 1 
    Stream #0:0[0x1011]: Video: h264 (High) (HDMV / 0x564D4448), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0:1[0x1100]: Audio: pcm_bluray (HDMV / 0x564D4448), 48000 Hz, stereo, s16, 1536 kb/s
    Stream #0:2[0x1101]: Audio: pcm_bluray (HDMV / 0x564D4448), 48000 Hz, 5.1(side), s16, 4608 kb/s
Output #0, wav, to 'Rattle Conducts Tchaikovsky, Stravinsky, Rachmaninov.wav':
  Metadata:
    encoder         : Lavf54.25.105
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 48000 Hz, 5.1, s16, 4608 kb/s
Stream mapping:
  Stream #0:2 -> #0:0 (pcm_bluray -> pcm_s16le)
  
  
  This is a 16-bit audio bluray   but if you had a 24-bit   which many  are  [i think!?]   you can retain that with any of the following settings   or upscale your 16-bit to 24


with

> ffmpeg -i 00000.m2ts -ac 6 -acodec pcm_s24le   24bitaudiofile.wav
  
  
 > DEA..S pcm_s32le            PCM signed 32-bit little-endian
 DEA..S pcm_s32be            PCM signed 32-bit big-endian
 DEA..S pcm_u32le            PCM unsigned 32-bit little-endian
 DEA..S pcm_u32be            PCM unsigned 32-bit big-endian
 DEA..S pcm_s24le            PCM signed 24-bit little-endian
 DEA..S pcm_s24be            PCM signed 24-bit big-endian
 DEA..S pcm_u24le            PCM unsigned 24-bit little-endian
 DEA..S pcm_u24be            PCM unsigned 24-bit big-endian
 DEA..S pcm_s24daud          PCM D-Cinema audio signed 24-bit   not all sure what the differences are between all of those


of course once you have your 6-channel wav you can go to 6-channel flac   using -ac 6 in the conversion line

---

