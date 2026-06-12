---
title: "intrepid ffmpeg mpeg4 ?"
date: 2008-11-20
forum: Multimedia Software
---

### Post by supertdog on 2008-11-20
Forgive me if the answer to this question is buried in this forum but I'm unable to find something clearly specific to this issue...

I am running ubuntu 8.10 (intrepid) x86_64

when I try to convert a video using ffmpeg to mpeg4 I get this error:

> Unknown encoder 'mpeg4'

this is the output from ffmpeg -formats

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 DE RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 D  apc             CRYO APC format
 D  ape             Monkey's Audio
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE avi             avi format
  E avm2            Flash 9 (AVM2) format
 D  avs             avs format
 D  bethsoftvid     Bethesda Softworks 'Daggerfall' VID format
 D  c93             Interplay C93
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  dxa             dxa
 D  ea              Electronic Arts Multimedia Format
 D  ea_cdata        Electronic Arts cdata
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
 D  libdc1394       dc1394 v.2 A/V grab
 D  lmlm4           lmlm4 raw format
 DE m4v             raw MPEG4 video format
 DE matroska        Matroska File Format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 D  mpc8            musepack8
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegtsraw       MPEG2 raw transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
 DE oss             audio grab and output
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 D  pva             pva file and stream format
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
 D  siff            Beam Software SIFF
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 D  txd             txd format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
 D  vc1test         VC1 test bitstream format
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
 D  x11grab         X11grab
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 D V D  aasc
  EA    ac3
 D A    adpcm_4xm
 DEA    adpcm_adx
 D A    adpcm_ct
 D A    adpcm_ea
 D A    adpcm_ea_r1
 D A    adpcm_ea_r2
 D A    adpcm_ea_r3
 D A    adpcm_ea_xas
 D A    adpcm_ima_amv
 D A    adpcm_ima_dk3
 D A    adpcm_ima_dk4
 D A    adpcm_ima_ea_eacs
 D A    adpcm_ima_ea_sead
 D A    adpcm_ima_qt
 D A    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 D A    adpcm_ima_ws
 DEA    adpcm_ms
 D A    adpcm_sbpro_2
 D A    adpcm_sbpro_3
 D A    adpcm_sbpro_4
 DEA    adpcm_swf
 D A    adpcm_thp
 D A    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 D V    amv
 D A    ape
 DEV D  asv1
 DEV D  asv2
 D A    atrac 3
 D V D  avs
 D V    bethsoftvid
 DEV    bmp
 D V D  c93
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 DEV D  dnxhd
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 D V    dxa
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 D V D  h261
 D VSDT h263
 D VSD  h263i
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
 DEV D  jpegls
 D V    kmvc
 D A    liba52
 D A    libfaad
 DEA    libgsm
 DEA    libgsm_ms
  EV    libtheora
  EA    libvorbis
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
 D A    mpc sv8
 DEVSDT mpeg1video
 D VSDT mpeg2video
 D VSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 D VSD  msmpeg4
 D VSD  msmpeg4v1
 D VSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D A    nellymoser
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 D A    pcm_s16le_planar
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
 DEA    pcm_zork
 D V    pcx
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V    ptx
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 DEV D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 DEA    roq_dpcm
 DEV D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 DEV    sgi
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 D V    sunrast
 DEV D  svq1
 D VSD  svq3
 DEV    targa
 D V    theora
 D V D  thp
 D V D  tiertexseqvideo
 DEV    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V    txd
 D V D  ultimotion
 D V    vb
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vp5
 D V D  vp6
 D V D  vp6a
 D V D  vp6f
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
 D S    xsub
 DEV D  zlib
 DEV    zmbv

Bitstream filters:
 text2movsub remove_extra noise mov2textsub mp3decomp mp3comp mjpegadump imxdump h264_mp4toannexb dump_extra
Supported file protocols:
 file: http: pipe: rtp: tcp: udp:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
```

do I need a particular repository?  How do I get mpeg4 support with ffmpeg on intrepid?

---

### Post by wolfen69 on 2008-11-20
go to synaptic and search for gstreamer good, bad and ugly. i'm sure one of those will give you mp4 support.

edit: isn't mpeg4 dvd format? anyway, if it is, you will need the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos. then do ```
sudo apt-get update
``` then ```
sudo apt-get install libdvdcss2
```

---

### Post by dantrevino on 2008-11-20
The ffmpeg in medibuntu seems to no longer exist.

---

### Post by FakeOutdoorsman on 2008-11-20
gstreamer and libdvdcss will do nothing to help you encode.  You need the ["unstripped" ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6207546&postcount=3").

---

### Post by supertdog on 2008-11-21
> **FakeOutdoorsman said:**
> gstreamer and libdvdcss will do nothing to help you encode.  You need the ["unstripped" ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6207546&postcount=3").

This seems to have helped, however, I now get the error:

>  Unknown encoder 'aac'   

which I thought should have been installed with the libavcodec-unstripped-51

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
```

---

### Post by supertdog on 2008-11-21
So it seems the script I was running was trying to encode with aac rather than libfaac.  When I switched this it seems to have made things work.  Thanks for your help.

---

### Post by penguinz on 2008-12-05
This solved my problem with MythExport.
First I had the Unknown encoder 'mpeg4'error 
--I had get the "unstripped" ffmpeg libraries.
Then I had the unknown encoder 'aac' error.
--I had to edit /usr/bin/mythexport and change all occurrences of aad to libfaac

now it exporting away

---

### Post by lingenfr on 2009-02-16
These instructions worked. I hate having to sift through a [SOLVED] post to find the actual solution, so I am highlighting it here:

> **FakeOutdoorsman said:**
> You need the ["unstripped" ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6207546&postcount=3").

> **penguinz said:**
> I had to edit /usr/bin/mythexport and change all occurrences of aac to libfaac

I am still testing to see if mythexport works now. If not I will try nuvexport. I noticed that when I purged ffmpeg as noted in the link, it also removed mytharchive which I reinstalled afterward.

---

### Post by ario on 2010-06-12
Ok! This is how I did it:
```
ffmpeg -i a.avi -s qcif -vcodec h263 -acodec libfaac -ac 1 -ar 44000 -r 25 -ab 32 -y b.3gp

```
Where a.avi is the input file and b.3gp is the output file.
It worked for me.

---

