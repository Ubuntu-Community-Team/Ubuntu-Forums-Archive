---
title: "convert to mpg4?"
date: 2008-10-15
forum: Multimedia Software
---

### Post by rapattack1 on 2008-10-15
Hi I have the medibuntu ffmpeg and winff it's gui installed and I want to convert movies to mpg4 that my mobile/cell phone can handle but I can't see what to select. I have mov's and avi's to convert. Is there a way?

---

### Post by stinger30au on 2008-10-17
one way would be to install virtual box and a copy of windows xp then install in to xp eright super

[http://www.erightsoft.com/SUPER.html](http://www.erightsoft.com/SUPER.html)


it will do what you want for free

---

### Post by rapattack1 on 2008-10-17
I have windows on my other machine so will install it there. 
I did notice though that when I recorded a video today that the format was 3gp and that is mentioned in winff. So I might try that first. Thanks!!!

---

### Post by rapattack1 on 2008-10-17
Ah I can't seem to convert to 3gp. The attachment is what i get. I tried to convert an mov and an mpg.

---

### Post by bttb on 2008-10-17
Hello,

you can give [avi2mp4.sh (Link)](http://forum.doom9.org/showthread.php?t=133598) a shot. The README only says what settings to use for iPods, but maybe you can figure out the ones for your phone.

Regards!

---

### Post by rapattack1 on 2008-10-17
I am afraid that page is way over my head. There is really not much I understood.

---

### Post by xc3RnbFO8P on 2008-10-17
Try [Avidemux]("http://www.getdeb.net/app/Avidemux")

---

### Post by rapattack1 on 2008-10-17
Ok I haven't got that installed so might add it to my Ubuntu Studio drive. Oh is Avidemux dependant on Jack because that damn app is a pain. I have been trying to get Jack happening for over a year and no one seems to stick at helping me. I even tried to coax a multimedia linux person over with a pizza and it didn't work. I am in Sydney.

OK well avidemux does convert the file nicely but the phone doesn't accept it. I checked by playing it in vlc that it is a valid file but maybe there is some tweaking to do. I am honestly new to messing with video files. I did do a beginner course in Final Cut Pro to help me but I have a lot to learn about converting video files.

---

### Post by FakeOutdoorsman on 2008-10-17
> **stinger30au said:**
> one way would be to install virtual box and a copy of windows xp then install in to xp eright super
There is no reason at all that anyone should need to install VirtualBox, install Windows in VirtualBox, and install SUPER to simply convert a video, especially since one of the tools SUPER uses is ffmpeg itself.

rapattack1, what mobile/cell do you have?  Each model can have its own particularities.  One option is to get a working video from the phone, and then use ffmpeg to see what options were used to encode it.  For example, this command:
```
ffmpeg -i video.flv
```
Gives the following info:
```
Input #0, flv, from 'video.flv':
Duration: 00:09:29.50, start: 0.000000, bitrate: 56 kb/s
Stream #0.0: Video: flv, yuv420p, 320x240, 29.97 tb(r)
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```
Now I can come up with a command using those parameters.  I can help you with that if we can't get WinFF to work.

The "unknown codec: libamr_nb" error you are getting is a result of ffmpeg changing its option names between revisions.  The WinFF presets are designed for a newer version of ffmpeg than what is in the Ubuntu or Medibuntu repositories.

The current WinFF preset for 3gp is:
```
-acodec libamr_nb  -ac 1  -vcodec h263 -s qcif -ar 8000 -r 25 -ab 12.2k
```
You need to change it to:
```
-acodec amr_nb  -ac 1  -vcodec h263 -s qcif -ar 8000 -r 25 -ab 12.2k
```
If you need to do this with other presets, you can see what ffmpeg names its codecs with:
```
ffmpeg -formats
```
As you can see, Medibuntu's ffmpeg is using "amr_nb", instead of "libamr_nb".

---

### Post by rapattack1 on 2008-10-17
Oh yes I am not willing to learn Virtual box or wine. I have reinstalled windows on my other machine that I use mainly for video surveillance and has a Hauppague card in it for watching/recording tv. It needed a new install anyway as windows gets so bogged down after a while.

I have a Samsung SGH-D500 and a video that I took the other day shows it is a 3gp but there was a downloaded video on the phone from the previous owner that was an mpeg. I deleted the mpeg because I wanted space. 
Ok will get onto my other drive that has the medibuntu thing and do the rest there. This drive that I am on right now has the ordinary ffmeg. I have a dual book situation. Ubuntu 8 on the primary and Ubuntustudio on the secondary.

Ok I got this:
poppinlockin@studio:~/Desktop$ ffmpeg -1 video-001.3gp
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg: unrecognized option '-1'
poppinlockin@studio:~/Desktop$ 

Dunno what went wrong here:
poppinlockin@studio:~$ -acodec amr_nb  -ac 1  -vcodec h263 -s qcif -ar 8000 -r 25 -ab 12.2k
bash: -acodec: command not found
poppinlockin@studio:~$ 

poppinlockin@studio:~$ ffmpeg -formats
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 D  RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
 D  avs             avs format
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw flac
 D  flic            FLI/FLC/FLX animation format
 DE flv             flv format
  E framecrc        framecrc testing format
 DE gif             GIF Animation
 DE gxf             GXF format
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 D  nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shorten
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  video4linux2    video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE voc             Creative Voice File format
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 DEA    aac
 D V D  aasc
 DEA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_sbpro_2
 DEA    adpcm_sbpro_3
 DEA    adpcm_sbpro_4
 DEA    adpcm_swf
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEA    amr_nb
 DEA    amr_wb
 DEV D  asv1
 DEV D  asv2
 D V D  avs
 DEV    bmp
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 DEA    gsm
 D A    gsm_ms
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 DEV DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    jpegls
 D V    kmvc
  EV    libtheora
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 D V D  mmvideo
 DEA    mp2
 DEA    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 D A    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 D V    targa
 D V    theora
 D V D  tiertexseqvideo
 D V    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V D  ultimotion
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V    vp5
 D V    vp6
 D V    vp6f
 D V D  vqavideo
 D A    wavpack
 DEA    wmav1
 DEA    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
  EV    xvid
 DEV D  zlib
 DEV    zmbv

Supported file protocols:
 file: pipe: udp: rtp: tcp: http:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1 hex umh iter

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported for example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats its even
worse


Yes I did notice a difference with the amr thing.

---

### Post by FakeOutdoorsman on 2008-10-21
> **rapattack1 said:**
> 
Ok I got this:
poppinlockin@studio:~/Desktop$ ffmpeg -1 video-001.3gp
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg: unrecognized option '-1'

You used an invalid command.  '-1' does nothing.  Try this instead:
```
ffmpeg -i video-001.3gp
```

> Dunno what went wrong here:
poppinlockin@studio:~$ -acodec amr_nb  -ac 1  -vcodec h263 -s qcif -ar 8000 -r 25 -ab 12.2k
bash: -acodec: command not found
This is just the preset settings for WinFF and is not a complete command.  You need to change WinFF's 3gp preset to the version I gave you and then run it from WinFF for this to work.

---

### Post by rapattack1 on 2008-10-21
OK I am a bit lost now but I did this:
carla@carla-desktop:~$ ffmpeg -i video-001.3gp
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
video-001.3gp: I/O error occured
Usually that means that input file is truncated and/or corrupted.
carla@carla-desktop:~$ 

I am sorry I don't know what the preset command is. It is over my head now.

---

### Post by hqconverter on 2008-10-22
I suggest u to find some suitable software at [http://www.dvdcreatormac.com](http://www.dvdcreatormac.com)

---

### Post by MKdx on 2008-10-22
Try this command:

```
ffmpeg -i MOV00006.MOV -s 176x144 -vcodec h263 -acodec aac -ab 64 -ar 8000 video-001.3gp
```

---

### Post by rapattack1 on 2008-10-22
Thanks MKdx we are closer to a good result. The good news is it converted to video and I was able to transfer it to the phone. I was also able to play it but the bad news is there was no audio. There is even a little audio icon on the phone and it had a stroke through it.

---

### Post by MKdx on 2008-10-22
My bad. Should've gone with amr codec here.

```
ffmpeg -i MOV00006.MOV -s 176x144 -vcodec h263 -acodec amr_nb -ac 1 -ar 8000 video-001.3gp
```

OR .. to avoid any confusion and problems later, just use QCIF (if it works for you).

```
ffmpeg -i MOV00006.MOV -s qcif -ac 1 -ar 8000 video-001.3gp
```

---

### Post by rapattack1 on 2008-10-23
Gee things are getting worse by the minute. I have had to delete dozens of bad files that were created. None of them are working with any command. I am able to transfer them to the phone but they only have video. No audio.
Also the studio machine is playing up(freezing) when I connect via bluetooth. Or not connect. Geez I give up. Or maybe another couple of days as I have too much work to do now.

---

### Post by Mr_bleu on 2009-10-06
**[COLOR="Red"]I can't get this to convert either.  I have no problems converting flv to mp3 though[/COLOR]**.  

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 8.00 (8/1)
Input #0, flv, from '/home/djr/Music/beutiful-bbw.flv':
  Duration: 00:06:50.49, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 500x375, 8 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 64 kb/s
Unable to find a suitable output format for '/dev/null'
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 8.00 (8/1)
Input #0, flv, from '/home/djr/Music/beutiful-bbw.flv':
  Duration: 00:06:50.49, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 500x375, 8 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 64 kb/s
Unknown encoder 'amr_nb'
Press Enter to Continue

---

