---
title: "mkv to mp4 for ipod: ipod can't play audo"
date: 2009-03-15
forum: Multimedia Software
---

### Post by djshaw on 2009-03-15
I have an mkv and I want to convert the file so that I can play it on my ipod.

However when I convert it to an mp4, the ipod does not play any sound. Additionally, the video does not automatically play after I select it; I have to press pause, then play before the video actually starts to play.

I am converting the mkv files with the command:

> 
ffmpeg -i input.mkv -f mp4 -vcodec libxvid -maxrate 1000 -qmin 4 -qmax 3 -bufsize 4096 -g 300 -acodec libfaac -s 480x320 -ab 128k -b 400k output.mkv


When I run the command, I get the following output

> 
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
[matroska @ 0xb7fde388]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0xb7fde388]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0xb7fde388]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0xb7fde388]Unknown entry 0x73a4 in info header
[matroska @ 0xb7fde388]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7fde388]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7fde388]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7fde388]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7fde388]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7fde388]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7fde388]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7fde388]Unknown track header entry 0xaa - ignoring
Input #0, matroska, from 'battlestar.galactica.s04e19.720p.hdtv.x264-ctu.mkv':
  Duration: 00:43:12.9, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: liba52, 48000 Hz, 5:1
    Stream #0.1(eng): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 23.98 tb(r)


I have tried using "-acodec aac", but I get the error "Unknown encoder 'aac'"

This problem occurs whenever I try to transcode a mkv file.

Does anyone know what is going on?

Thanks





Just in case:
> 
 ffmpeg -formats
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
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
 DEV D  jpegls
 D V    kmvc
 D A    liba52
  EA    libfaac
 D A    libfaad
 DEA    libgsm
 DEA    libgsm_ms
  EA    libmp3lame
  EV    libtheora
  EA    libvorbis
  EV    libx264
  EV    libxvid
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

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.



---

### Post by FakeOutdoorsman on 2009-03-15
There are many ways to encode video for iPod, but I'll tell you how to do it with a recent version of FFmpeg.  The revision of FFmpeg from the Ubuntu repository is ancient and there have been thousands of updates since then.

1. Follow this tutorial:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

2. The FFmpeg command.  This example uses one-pass CRF.  A lower crf value is a higher quality, but a larger file size:
```
ffmpeg -i input.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -vpre ipod640 -s 640x360 -threads 0 -crf 26 output.mp4
```
I recommend a quick ten-second test encode to make sure everything works by adding "-t 10" to the above command.

3. I don't think this step is necessary for the video to play on the iPod (unless you are using iTunes), but it will add the appropriate metadata.  First install atomicparsley:
```
sudo apt-get install atomicparsley
```
Now the command (I haven't tested this in Ubuntu: you may have to compile AtomicParsley from SVN if this doesn't work):
```
AtomicParsley output.mp4 --DeepScan --iPod-uuid 1200 --overWrite --title "Battlestar Galactica" --year "2008"--TVNetwork "SciFi" --TVShowName "Battlestar Galactica" --TVSeasonNum 4 --TVEpisodeNum 19
```

---

