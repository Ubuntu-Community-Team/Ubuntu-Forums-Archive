---
title: "problems converting video with mp4ize, libxvid"
date: 2008-11-11
forum: Multimedia Software
---

### Post by fINTiP on 2008-11-11
I'm trying to use [mp4ize]("http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html"), and I've been following the ubuntu unleashed tutorial linked to above. 

I'm stuck here, any ideas?

```
kajo@dasg:~/Desktop/Multimedia/movie/Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR$ mp4ize Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'xvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'libxvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'libxvid'
```

I'm in 8.04 studio, and I have the medibuntu FFMPEG installed

K

---

### Post by FakeOutdoorsman on 2008-11-11
Show the complete output of:
```
ffmpeg -formats
```

---

### Post by fINTiP on 2008-11-12
```
user@computer:~$ ffmpeg -formats
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
 D V D  aasc
  EA    ac3
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
 D V DT h264
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
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
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

```

---

### Post by FakeOutdoorsman on 2008-11-12
Your version of ffmpeg doesn't have many of the restricted formats enabled.  I'm not very familiar with Medibuntu's ffmpeg.  Your ffmpeg version looks like it's from Medibuntu, but the listed codecs are the same as ffmpeg from the Ubuntu repository.  The command "aptitude show ffmpeg" should give you:
```
Package: ffmpeg
State: installed
Automatically installed: yes
Version: 3:0.cvs20070307-5ubuntu7.1+medibuntu1
Priority: optional
Section: free/graphics
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Uncompressed Size: 680k
Depends: libavcodec1d (>= 0.cvs20070307), libavformat1d (>= 0.cvs20070307),
         libavutil1d (>= 0.cvs20070307), libc6 (>= 2.7), libfreetype6 (>=
         2.3.5), libimlib2, libsdl1.2debian (>= 1.2.10-1), libswscale1d (>=
         0.cvs20070307)
Description: multimedia player, server and encoder - Medibuntu package
 This package contains the ffplay multimedia player, the ffserver streaming
 server and the ffmpeg audio and video encoder. They support most existing file
 formats (AVI, MPEG, OGG, Matroska, ASF...) and encoding formats (MPEG, DivX,
 MPEG4, AC3, DV...). 
 
 This package is built with the "risky" option, to enable mp3/mp4/h264/amr
 support. Therefore, it is in Medibuntu as it might violate patents. 
 
 This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU! 
 
 Please report any bug to our bug tracker instead: 
 https://bugs.launchpad.net/medibuntu/+bugs
```

---

### Post by fINTiP on 2008-11-12
I am also using floola, and because medibuntu's ffmpeg has h264 and acc support, I was told to use that version.

FFMPEG is a giant mystery to me. It's not working for floola, either- that's another issue I'm currently trying to work out.

the only difference between my output of 'aptitude ffmpeg show' and yours was this line:

```
Section: graphics
```

instead of free/graphics.

Whatever should I do? What's more, what exactly is going on?

L

---

### Post by FakeOutdoorsman on 2008-11-13
I'm not sure what is going on with your installation.  It's probably something obvious, but I'm missing it.  You could always try to remove your current ffmpeg and then make sure you're installing Medibuntu's version and it's dependencies:

1. Remove ffmpeg:
```
sudo apt-get autoremove ffmpeg
```
2. Check to see the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") is added (you can probably also do this in System -> Administration -> Software Sources).

3. Update your sources.list:
```
sudo apt-get update
```
4. Reinstall ffmpeg and make sure it's Medibuntu's version.  You can do this in Synaptic Package Manager, select ffmpeg, and then choose the Package menu -> Force Version.  I think...  I don't use Synaptic.

---

### Post by fINTiP on 2008-11-15
I followed those instructions. My current output for "ffmpeg -formats" is this:
```
kajo@dasg:~$ ffmpeg -formats
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
 D V D  aasc
  EA    ac3
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
 D V DT h264
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
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
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
```

Is everything better?
Should I reinstall mp4ize from scratch?

L

---

### Post by fINTiP on 2008-11-15
Also, when I try to use mp4ize, here is my current output (I don't think it changed? It still doesn't work. :\ )

```
kajo@dasg:~/Desktop/Multimedia/movie/Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR$ mp4ize Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi 
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'xvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'libxvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'libxvid'
```

L

---

### Post by FakeOutdoorsman on 2008-11-15
I don't get it.  I installed Medibuntu's ffmpeg on a stock install of Hardy and I have the correct formats available, while you don't.  Another option is to uninstall Medibuntu's ffmpeg compile ffmpeg yourself.

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

If you follow the above tutorial, and since your script uses libxvid, you will need to install libxvidcore4-dev along with all of the other packages on step 2.  On step 5, your ffmpeg configure line will need "--enable-libxvid" as well, so it might look like:
```
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
```

---

### Post by fINTiP on 2008-11-16
So, the update manager just asked me to update, and had a lot of ffmpeg medibuntu stuff listed. I thought I'd post the current output and ask if it was different, being as this is all gibberish to me and I can't read it myself.

Should I still try doing it from source?

```
user@comp:~$ ffmpeg -formats
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

```

:confused:

L

---

### Post by fINTiP on 2008-11-16
Also, [medibuntu's?] mplayer wanted to be installed in the update manager also, I think... so I thought I might try and just watch the movie with mplayer, because it seems to rely on ffmpeg's codecs, or something...

...anyways, mplayer will only play the audio of [at least] the avi in question. Totem is able to play it fine, by comparison.

I am so lost as to what is going on... I don't understand why multimedia is so difficult to get working on Ubuntu. :?

L

---

### Post by FakeOutdoorsman on 2008-11-16
> **fINTiP said:**
> So, the update manager just asked me to update, and had a lot of ffmpeg medibuntu stuff listed. I thought I'd post the current output and ask if it was different, being as this is all gibberish to me and I can't read it myself.

Should I still try doing it from source?

```
user@comp:~$ ffmpeg -formats
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

```

:confused:

L

This looks right because xvid and some other codecs are now available.  I think the script will work now.

---

### Post by fINTiP on 2008-11-17
It does.

Thanks, this is a huge help to me. 

If you could be so bothered, could you explain what all happened here?

L

---

### Post by FakeOutdoorsman on 2008-11-18
I don't really know what the deal was.  It seems like your package index files were never synched up (apt-get update) to the repositories that you have enabled.

---

### Post by fINTiP on 2008-11-18
Odd.

Well, one more thing- I want to now be able to do this in Nautilus via right-clicking on a file.

The instructions on how to do this are a bit cryptic to me, though- in the main instructions, it says this:

> Now, if you want to convert a video, just open up a terminal and type mp4ize [videoname] and it will make an IPod mp4 version in the same folder. **Enterprising Nautilus Actions users may want to add a right click menu version for this by adding /usr/local/bin/mp4ize as a path and %M as a parameter.**

And someone in the comments says something equally cryptic-

```
Simply create a file in $HOME/.gnome2/nautilus-scripts/toIpodFormat

Which contains:

#!/bin/bash

for i in "$@"; do

/usr/local/bin/mp4ize "$i"

done

Also make it executable with

chmod a+rx $HOME/.gnome2/nautilus-scripts/toIpodFormat

Have fun! 
```

What am I to do?

L

---

### Post by FakeOutdoorsman on 2008-11-18
> **fINTiP said:**
> Odd.

Well, one more thing- I want to now be able to do this in Nautilus via right-clicking on a file.
I don't have Nautilus, but to use the first option, you need to install **nautilus-actions**.  I have no experience with it.


> 
And someone in the comments says something equally cryptic-

```
Simply create a file in $HOME/.gnome2/nautilus-scripts/toIpodFormat

Which contains:

#!/bin/bash

for i in "$@"; do

/usr/local/bin/mp4ize "$i"

done

Also make it executable with

chmod a+rx $HOME/.gnome2/nautilus-scripts/toIpodFormat

Have fun! 
```

What am I to do?

L
For this option:
1. Open a text editor, and dump the following text into it:
```
#!/bin/bash

for i in "$@"; do

/usr/local/bin/mp4ize "$i"

done
```
2. Save this file as toIpodFormat.  It needs to go into the ~/.gnome2/nautilus-scripts/ folder.  The "~/" part means "your home folder" and is similar to $HOME.  Since .gnome2 is preceded with a period, it is a hidden folder.  To see this folder in Nautilus, use ctrl + h, or if you are in a terminal type "ls -a".

3. Now you need to make sure the toIpodFormat script is executable by the system.  Navigate to the file in Nautilus, right click, choose Properties -> Permissions tab, and check "Allow executing file as program".  If you like to use a terminal instead, then open a terminal and enter:
```
chmod +x ~/.gnome2/nautilus-scripts/toIpodFormat
```
4. Now if you right click on the file, you should get a "Scripts" menu with toIpodFormat in it.  You may have to close Nautilus and restart it to show the new scripts menu.

---

### Post by kiyodaira on 2009-05-27
I installed ffmpeg from Midibuntu and then did apt-get upgrade to upgrade some packages which likely come from midibuntu, and finally the mp4ize script ran. Thanks all.

---

