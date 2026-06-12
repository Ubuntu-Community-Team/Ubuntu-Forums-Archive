---
title: "VLC can't encode to MP3"
date: 2012-06-08
forum: Multimedia Software
---

### Post by c-m on 2012-06-08
In linux mint i used to use VLC to record radio streams to mp3.

I have tried the same since switching to Ubuntu 12.04, but I get an error saying MP3 encoding isn't available in my fmpeg package - or something to that affect.

How do I solve this issue?

Thanks

---

### Post by Enigmapond on 2012-06-08
Why are you trying to encode with VLC? If you want a simple GUI for that use soundconverter. What is the source file?

---

### Post by c-m on 2012-06-08
Because I then play it in vlc too so it's delayed. Besides I already have VLC installed and the process worked great in Mint. I just want to replicate that. 

No doubt Ubuntu is missing some important encoder, but I don't know which one, hence can't install it.

The source file is bbc radio so .asx steam

---

### Post by fixitdude on 2012-06-08
Might be that you need to turn on the restricted or non-free repositories and install lame or liblame - off the top of my head, maybe do a quick google on those.

I think if you install all the multimedia stuff people recommend here you will be back to normal, you have to do that after every upgrade it seems.

---

### Post by flemur13013 on 2012-06-08
This mp3 stuff has been a PITA - until 12.04, where it seemed easier.

You might need these (from synaptic or apt-get):

gstreamer0.10-plugins-ugly

and maybe:

gstreamer0.10-plugins-bad
libgstreamer-plugins-bad0.10-0

---

### Post by shantiq on 2012-06-08
```
sudo apt-get install lame
```   installs mp3   



  or go to synaptic and add lame



and to check your ffmpeg has the right formats run


> ffmpeg  -formats    see if you have

>   E mov             MOV format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG-4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
[B] DE mp3             MPEG audio layer 3                          [ [COLOR="Red"]D for decode E for encode[/COLOR]]
[/B]  E mp4             MP4 format
 D  mpc             Musepack
 D  mpc8            Musepack SV8
 DE mpeg            MPEG-1 System format
  E mpeg1video      raw MPEG-1 video


---

### Post by c-m on 2012-06-08
> **flemur13013 said:**
> This mp3 stuff has been a PITA - until 12.04, where it seemed easier.

You might need these (from synaptic or apt-get):

gstreamer0.10-plugins-ugly

and maybe:

gstreamer0.10-plugins-bad
libgstreamer-plugins-bad0.10-0

Thanks guys, but I already have all of those anyway.


@shantiq
Lame - says it's just a front end, and doesn't install any other packages.

Yep I also have > DE mp3 MPEG audio layer 3


---

### Post by shantiq on 2012-06-08
ok so if your record a radio station    [with red button]    you are finding it does not leave an mp3 file in your Music folder right?


what happens ?


do you get anything?   an aac?      please explain a little more..

---

### Post by c-m on 2012-06-08
This is in VLC, there is no red record button. I'm doing a convert/save.

Here is the exact error message:

```
Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG I/II Layer 3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.
```

.ogg works fine so I can use that for now.


```

$ ffmpeg -formats
ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
File formats:
 D. = Demuxing supported
 .E = Muxing supported
 --
  E 3g2             3GP2 format
  E 3gp             3GP format
 D  4xm             4X Technologies format
 D  IFF             IFF format
 D  ISS             Funcom ISS format
 D  MTV             MTV format
 DE RoQ             raw id RoQ format
  E a64             a64 - video for Commodore 64
 D  aac             raw ADTS AAC
 DE ac3             raw AC-3
  E adts            ADTS AAC
 DE adx             CRI ADX
 D  aea             MD STUDIO audio
 DE aiff            Audio IFF
 DE alaw            PCM A-law format
 DE alsa            ALSA audio output
 DE amr             3GPP AMR file format
 D  anm             Deluxe Paint Animation
 D  apc             CRYO APC format
 D  ape             Monkey's Audio
 D  applehttp       Apple HTTP Live Streaming format
 DE asf             ASF format
  E asf_stream      ASF format
 DE ***             Advanced SubStation Alpha subtitle format
 DE au              SUN AU format
 DE avi             AVI format
  E avm2            Flash 9 (AVM2) format
 D  avs             AVS format
 D  bethsoftvid     Bethesda Softworks VID format
 D  bfi             Brute Force & Ignorance
 D  bink            Bink
 D  bmv             Discworld II BMV
 D  c93             Interplay C93
 D  caf             Apple Core Audio Format
 DE cavsvideo       raw Chinese AVS video
 D  cdg             CD Graphics Format
  E crc             CRC testing format
 DE daud            D-Cinema audio format
 D  dfa             Chronomaster DFA
 DE dirac           raw Dirac
 DE dnxhd           raw DNxHD (SMPTE VC-3)
 D  dsicin          Delphine Software International CIN format
 DE dts             raw DTS
 DE dv              DV video format
 D  dv1394          DV1394 A/V grab
  E dvd             MPEG-2 PS format (DVD VOB)
 D  dxa             DXA
 D  ea              Electronic Arts Multimedia Format
 D  ea_cdata        Electronic Arts cdata
 DE eac3            raw E-AC-3
 DE f32be           PCM 32 bit floating-point big-endian format
 DE f32le           PCM 32 bit floating-point little-endian format
 DE f64be           PCM 64 bit floating-point big-endian format
 DE f64le           PCM 64 bit floating-point little-endian format
 D  fbdev           Linux framebuffer
 DE ffm             FFM (AVserver live feed) format
 DE ffmetadata      FFmpeg metadata in text format
 D  film_cpk        Sega FILM/CPK format
 DE filmstrip       Adobe Filmstrip
 DE flac            raw FLAC
 D  flic            FLI/FLC/FLX animation format
 DE flv             FLV format
  E framecrc        framecrc testing format
  E framemd5        Per-frame MD5 testing format
 DE g722            raw G.722
  E gif             GIF Animation
 D  gsm             raw GSM
 DE gxf             GXF format
 DE h261            raw H.261
 DE h263            raw H.263
 DE h264            raw H.264 video format
 D  idcin           id Cinematic format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       raw Ingenient MJPEG
 D  ipmovie         Interplay MVE format
  E ipod            iPod H.264 MP4 format
 D  iv8             A format generated by IndigoVision 8000 video server
 DE ivf             On2 IVF
 D  jack            JACK Audio Connection Kit
 D  jv              Bitmap Brothers JV
 DE latm            LOAS/LATM
 D  libdc1394       dc1394 v.2 A/V grab
 D  lmlm4           lmlm4 raw format
 D  lxf             VR native stream format (LXF)
 DE m4v             raw MPEG-4 video format
  E matroska        Matroska file format
 D  matroska,webm   Matroska/WebM file format
  E md5             MD5 testing format
 DE mjpeg           raw MJPEG video
 DE mlp             raw MLP
 D  mm              American Laser Games MM format
 DE mmf             Yamaha SMAF
  E mov             MOV format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG-4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             MP4 format
 D  mpc             Musepack
 D  mpc8            Musepack SV8
 DE mpeg            MPEG-1 System format
  E mpeg1video      raw MPEG-1 video
  E mpeg2video      raw MPEG-2 video
 DE mpegts          MPEG-2 transport stream format
 D  mpegtsraw       MPEG-2 raw transport stream format
 D  mpegvideo       raw MPEG video
  E mpjpeg          MIME multipart JPEG format
 D  msnwctcp        MSN TCP Webcam stream
 DE mulaw           PCM mu-law format
 D  mvi             Motion Pixels MVI format
 DE mxf             Material eXchange Format
  E mxf_d10         Material eXchange Format, D-10 Mapping
 D  mxg             MxPEG clip file format
 D  nc              NC camera feed format
 D  nsv             Nullsoft Streaming Video
  E null            raw null video format
 DE nut             NUT format
 D  nuv             NuppelVideo format
 DE ogg             Ogg
 DE oma             Sony OpenMG audio
 DE oss             Open Sound System playback
 D  pmp             Playstation Portable PMP format
  E psp             PSP MP4 format
 D  psxstr          Sony Playstation STR format
 D  pva             TechnoTrend PVA file and stream format
 D  qcp             QCP format
 D  r3d             REDCODE R3D format
 DE rawvideo        raw video format
  E rcv             VC-1 test bitstream
 D  rl2             RL2 format
 DE rm              RealMedia format
 D  rpl             RPL/ARMovie format
 DE rso             Lego Mindstorms RSO format
 DE rtp             RTP output format
 DE rtsp            RTSP output format
 DE s16be           PCM signed 16 bit big-endian format
 DE s16le           PCM signed 16 bit little-endian format
 DE s24be           PCM signed 24 bit big-endian format
 DE s24le           PCM signed 24 bit little-endian format
 DE s32be           PCM signed 32 bit big-endian format
 DE s32le           PCM signed 32 bit little-endian format
 DE s8              PCM signed 8 bit format
 DE sap             SAP output format
 D  sdp             SDP
  E segment         segment muxer
 D  shn             raw Shorten
 D  siff            Beam Software SIFF
 DE smjpeg          Loki SDL MJPEG
 D  smk             Smacker video
 D  sol             Sierra SOL format
 DE sox             SoX native format
 DE spdif           IEC 61937 (used on S/PDIF - IEC958)
 DE srt             SubRip subtitle format
  E svcd            MPEG-2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tmv             8088flex TMV
 DE truehd          raw TrueHD
 D  tta             True Audio
 D  tty             Tele-typewriter
 D  txd             Renderware TeXture Dictionary
 DE u16be           PCM unsigned 16 bit big-endian format
 DE u16le           PCM unsigned 16 bit little-endian format
 DE u24be           PCM unsigned 24 bit big-endian format
 DE u24le           PCM unsigned 24 bit little-endian format
 DE u32be           PCM unsigned 32 bit big-endian format
 DE u32le           PCM unsigned 32 bit little-endian format
 DE u8              PCM unsigned 8 bit format
 D  vc1             raw VC-1
 D  vc1test         VC-1 test bitstream format
  E vcd             MPEG-1 System format (VCD)
 D  video4linux2    Video4Linux2 device grab
 D  vmd             Sierra VMD format
  E vob             MPEG-2 PS format (VOB)
 DE voc             Creative Voice file format
 D  vqf             Nippon Telegraph and Telephone Corporation (NTT) TwinVQ
 D  w64             Sony Wave64 format
 DE wav             WAV format
 D  wc3movie        Wing Commander III movie format
  E webm            WebM file format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wtv             Windows Television (WTV)
 D  wv              WavPack
 D  x11grab         X11grab
 D  xa              Maxis XA File Format
 D  xmv             Microsoft XMV
 D  xwma            Microsoft xWMA
 D  yop             Psygnosis YOP Format
 DE yuv4mpegpipe    YUV4MPEG pipe format


```

---

### Post by shantiq on 2012-06-08
i see.     so just tested it on my system    also pangolin


and it went fine .   so see what you have as libavcodec in your synaptic



it looks this way on my system [ATTACH]219407[/ATTACH]


see if it is different your side   if you find you have libavcodec53   change it for libavcodec-extra-53    and this should very likely add functionality you seek

**actually**   before you even do that check and see if you have  libmp3lame0  installed [ATTACH]219408[/ATTACH]


since that is the one contained in libavcodec-extra-53 which allows one to convert from and to mp3   [and it is not present in the libavcodec53 more basic package

see here       [ATTACH]219410[/ATTACH]     you probably will find   only adding    **libmp3lame0**   will swing it otherwise  go for the full extra package libavcodec-extra-53      Hope this is clear   enugh  ::::]]]

---

### Post by HiWayChile on 2012-08-14
Thank You!
I had the same problem. This made the trick for me. I had libmp3lame0 installed, but replaced libavcodec53 to libavcodec-extra-53 and got it to work finally.

> **shantiq said:**
> i see.     so just tested it on my system    also pangolin


and it went fine .   so see what you have as libavcodec in your synaptic



it looks this way on my system [ATTACH]219407[/ATTACH]


see if it is different your side   if you find you have libavcodec53   change it for libavcodec-extra-53    and this should very likely add functionality you seek

**actually**   before you even do that check and see if you have  libmp3lame0  installed [ATTACH]219408[/ATTACH]


since that is the one contained in libavcodec-extra-53 which allows one to convert from and to mp3   [and it is not present in the libavcodec53 more basic package

see here       [ATTACH]219410[/ATTACH]     you probably will find   only adding    **libmp3lame0**   will swing it otherwise  go for the full extra package libavcodec-extra-53      Hope this is clear   enugh  ::::]]]

---

### Post by carra on 2012-09-28
Thanks a lot. :p
It did the trick for me too. :guitar:


> **shantiq said:**
> i see.     so just tested it on my system    also pangolin


and it went fine .   so see what you have as libavcodec in your synaptic



it looks this way on my system [ATTACH]219407[/ATTACH]


see if it is different your side   if you find you have libavcodec53   change it for libavcodec-extra-53    and this should very likely add functionality you seek

**actually**   before you even do that check and see if you have  libmp3lame0  installed [ATTACH]219408[/ATTACH]


since that is the one contained in libavcodec-extra-53 which allows one to convert from and to mp3   [and it is not present in the libavcodec53 more basic package

see here       [ATTACH]219410[/ATTACH]     you probably will find   only adding    **libmp3lame0**   will swing it otherwise  go for the full extra package libavcodec-extra-53      Hope this is clear   enugh  ::::]]]

---

### Post by Davwan on 2012-10-28
Thanks... Worked for me too in linux mint maya.

---

### Post by nmsalgueiro on 2013-01-04
This also worked for me in 12.10. Thank you!

---

### Post by DrDaveHPP on 2013-02-17
> **shantiq said:**
> if you find you have libavcodec53 change it for libavcodec-extra-53 and this should very likely add functionality you seek
Worked for me in Mint 14 x64 too. Many thanks!

---

### Post by dbruvers on 2013-03-02
On my machine **libmp3lame0** was already installed. Installing** libavcodec-extra-53** fixed it for me on Ubuntu 12.10. Thank you!

---

### Post by van hanegen on 2013-03-12
At least i can convert CD's to MP3 without installing any additional apps (12.10)
Thanks a lot!!!

---

### Post by Joe Question on 2013-03-27
Thank you soooo much! Worked for me too, I had the libmp3lame0 but to make it work had to replace libavcodec53 for libavcodec-extra-53

---

