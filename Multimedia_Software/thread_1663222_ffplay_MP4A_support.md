---
title: "ffplay MP4A support"
date: 2011-01-09
forum: Multimedia Software
---

### Post by x53x6ex69x67x67x65x72 on 2011-01-09
Hi
I'm using Kaffeine to view DVB-T channels .
It uses FFPLAY to play video.
The video shows correctly but there is no audio. 
mplayer plays it's recorded file correctly (with sound)
but ffplay just shows video and there is no sound.
Here is my ffplay configuration during compile:
```
 configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264 --enable-nonfree
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep  5 2010 15:27:14, gcc: 4.4.3

```and this is it's formats:
```
File formats:
  E 3g2             3GP2 format
  E 3gp             3GP format
 D  4xm             4X Technologies format
 D  IFF             IFF format
 D  ISS             Funcom ISS format
 D  MTV             MTV format
 DE RoQ             raw id RoQ format
 D  aac             raw ADTS AAC
 DE ac3             raw AC-3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            PCM A-law format
 DE alsa            ALSA audio output
 DE amr             3GPP AMR file format
 D  apc             CRYO APC format
 D  ape             Monkey's Audio
 DE asf             ASF format
  E asf_stream      ASF format
 DE ***             SSA/*** format
 DE au              SUN AU format
 DE avi             AVI format
  E avm2            Flash 9 (AVM2) format
 D  avs             AVS format
 D  bethsoftvid     Bethesda Softworks VID format
 D  bfi             Brute Force & Ignorance
 D  c93             Interplay C93
 D  cavsvideo       raw Chinese AVS video
  E crc             CRC testing format
 DE daud            D-Cinema audio format
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
 DE ffm             FFM (FFserver live feed) format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw FLAC
 D  flic            FLI/FLC/FLX animation format
 DE flv             FLV format
  E framecrc        framecrc testing format
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
 D  libdc1394       dc1394 v.2 A/V grab
 D  lmlm4           lmlm4 raw format
 DE m4v             raw MPEG-4 video format
 DE matroska        Matroska file format
 DE mjpeg           raw MJPEG video
 D  mlp             raw MLP
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
 D  nc              NC camera feed format
 D  nsv             Nullsoft Streaming Video
  E null            raw null video format
 DE nut             NUT format
 D  nuv             NuppelVideo format
 DE ogg             Ogg
 D  oma             Sony OpenMG audio
 DE oss             Open Sound System playback
  E psp             PSP MP4 format
 D  psxstr          Sony Playstation STR format
 D  pva             TechnoTrend PVA file and stream format
 D  r3d             REDCODE R3D format
 DE rawvideo        raw video format
  E rcv             VC-1 test bitstream
 D  redir           Redirector format
 D  rl2             RL2 format
 DE rm              RealMedia format
 D  rpl             RPL/ARMovie format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           PCM signed 16 bit big-endian format
 DE s16le           PCM signed 16 bit little-endian format
 DE s24be           PCM signed 24 bit big-endian format
 DE s24le           PCM signed 24 bit little-endian format
 DE s32be           PCM signed 32 bit big-endian format
 DE s32le           PCM signed 32 bit little-endian format
 DE s8              PCM signed 8 bit format
 D  sdp             SDP
 D  shn             raw Shorten
 D  siff            Beam Software SIFF
 D  smk             Smacker video
 D  sol             Sierra SOL format
  E svcd            MPEG-2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             True Audio
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
 D  video4linux     Video4Linux device grab
 D  video4linux2    Video4Linux2 device grab
 D  vmd             Sierra VMD format
  E vob             MPEG-2 PS format (VOB)
 DE voc             Creative Voice file format
 DE wav             WAV format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 D  xa              Maxis XA File Format
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm             4X Movie
 D V D  8bps            QuickTime 8BPS video
 D A    8svx_exp        8SVX exponential
 D A    8svx_fib        8SVX fibonacci
 D A    aac             Advanced Audio Coding
 D V D  aasc            Autodesk RLE
 DEA    ac3             ATSC A/52A (AC-3)
 D A    adpcm_4xm       ADPCM 4X Movie
 DEA    adpcm_adx       SEGA CRI ADX ADPCM
 D A    adpcm_ct        ADPCM Creative Technology
 D A    adpcm_ea        ADPCM Electronic Arts
 D A    adpcm_ea_maxis_xa ADPCM Electronic Arts Maxis CDROM XA
 D A    adpcm_ea_r1     ADPCM Electronic Arts R1
 D A    adpcm_ea_r2     ADPCM Electronic Arts R2
 D A    adpcm_ea_r3     ADPCM Electronic Arts R3
 D A    adpcm_ea_xas    ADPCM Electronic Arts XAS
 D A    adpcm_ima_amv   ADPCM IMA AMV
 D A    adpcm_ima_dk3   ADPCM IMA Duck DK3
 D A    adpcm_ima_dk4   ADPCM IMA Duck DK4
 D A    adpcm_ima_ea_eacs ADPCM IMA Electronic Arts EACS
 D A    adpcm_ima_ea_sead ADPCM IMA Electronic Arts SEAD
 D A    adpcm_ima_iss   ADPCM IMA Funcom ISS
 DEA    adpcm_ima_qt    ADPCM IMA QuickTime
 D A    adpcm_ima_smjpeg ADPCM IMA Loki SDL MJPEG
 DEA    adpcm_ima_wav   ADPCM IMA WAV
 D A    adpcm_ima_ws    ADPCM IMA Westwood
 DEA    adpcm_ms        ADPCM Microsoft
 D A    adpcm_sbpro_2   ADPCM Sound Blaster Pro 2-bit
 D A    adpcm_sbpro_3   ADPCM Sound Blaster Pro 2.6-bit
 D A    adpcm_sbpro_4   ADPCM Sound Blaster Pro 4-bit
 DEA    adpcm_swf       ADPCM Shockwave Flash
 D A    adpcm_thp       ADPCM Nintendo Gamecube THP
 D A    adpcm_xa        ADPCM CDROM XA
 DEA    adpcm_yamaha    ADPCM Yamaha
 DEA    alac            ALAC (Apple Lossless Audio Codec)
 D V    amv             AMV Video
 D A    ape             Monkey's Audio
 DEV D  asv1            ASUS V1
 DEV D  asv2            ASUS V2
 D A    atrac3          Atrac 3 (Adaptive TRansform Acoustic Coding 3)
 D V D  avs             AVS (Audio Video Standard) video
 D V    bethsoftvid     Bethesda VID video
 D V    bfi             Brute Force & Ignorance
 DEV    bmp             BMP image
 D V D  c93             Interplay C93
 D V D  camstudio       CamStudio
 D V D  camtasia        TechSmith Screen Capture Codec
 D V D  cavs            Chinese AVS video (AVS1-P2, JiZhun profile)
 D V D  cinepak         Cinepak
 D V D  cljr            Cirrus Logic AccuPak
 D A    cook            COOK
 D V D  cyuv            Creative YUV (CYUV)
 D A    dca             DCA (DTS Coherent Acoustics)
 DEV D  dnxhd           VC3/DNxHD
 D A    dsicinaudio     Delphine Software International CIN audio
 D V D  dsicinvideo     Delphine Software International CIN video
 DES    dvbsub          DVB subtitles
 DES    dvdsub          DVD subtitles
 DEV D  dvvideo         DV (Digital Video)
 D V    dxa             Feeble Files/ScummVM DXA
 D A    eac3            ATSC A/52B (AC-3, E-AC-3)
 D V D  eacmv           Electronic Arts CMV video
 D V D  eatgq           Electronic Arts TGQ video
 D V    eatgv           Electronic Arts TGV video
 D V D  eatqi           Electronic Arts TQI Video
 D V D  escape124       Escape 124
 DEV D  ffv1            FFmpeg codec #1
 DEVSD  ffvhuff         Huffyuv FFmpeg variant
 DEA    flac            FLAC (Free Lossless Audio Codec)
 DEV D  flashsv         Flash Screen Video
 D V D  flic            Autodesk Animator Flic video
 DEVSD  flv             Flash Video (FLV)
 D V D  fraps           Fraps
 DEA    g726            G.726 ADPCM
 DEV    gif             GIF (Graphics Interchange Format)
 DEV D  h261            H.261
 DEVSDT h263            H.263 / H.263-1996
 D VSD  h263i           Intel H.263
  EV    h263p           H.263+ / H.263-1998 / H.263 version 2
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 DEVSD  huffyuv         Huffyuv / HuffYUV
 D V D  idcinvideo      id Quake II CIN video
 D A    imc             IMC (Intel Music Coder)
 D V D  indeo2          Intel Indeo 2
 D V    indeo3          Intel Indeo 3
 D A    interplay_dpcm  DPCM Interplay
 D V D  interplayvideo  Interplay MVE video
 DEV D  jpegls          JPEG-LS
 D V    kmvc            Karl Morton's video codec
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
 D A    libfaad         libfaad AAC (Advanced Audio Codec)
 DEA    libgsm          libgsm GSM
 DEA    libgsm_ms       libgsm GSM Microsoft variant
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EV    libxvid         libxvidcore MPEG-4 part 2
  EV    ljpeg           Lossless JPEG
 D V D  loco            LOCO
 D A    mace3           MACE (Macintosh Audio Compression/Expansion) 3:1
 D A    mace6           MACE (Macintosh Audio Compression/Expansion) 6:1
 D V D  mdec            Sony PlayStation MDEC (Motion DECoder)
 D V D  mimic           Mimic
 DEV D  mjpeg           MJPEG (Motion JPEG)
 D V D  mjpegb          Apple MJPEG-B
 D A    mlp             MLP (Meridian Lossless Packing)/TrueHD
 D V D  mmvideo         American Laser Games MM Video
 D V D  motionpixels    Motion Pixels video
 D A    mp1             MP1 (MPEG audio layer 1)
 DEA    mp2             MP2 (MPEG audio layer 2)
 D A    mp3             MP3 (MPEG audio layer 3)
 D A    mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3on4          MP3onMP4
 D A    mpc7            Musepack SV7
 D A    mpc8            Musepack SV8
 DEVSDT mpeg1video      MPEG-1 video
 DEVSDT mpeg2video      MPEG-2 video
 DEVSDT mpeg4           MPEG-4 part 2
 D VSDT mpegvideo       MPEG-1 video
 D VSDT mpegvideo_xvmc  MPEG-1/2 video XvMC (X-Video Motion Compensation)
 DEVSD  msmpeg4         MPEG-4 part 2 Microsoft variant version 3
 DEVSD  msmpeg4v1       MPEG-4 part 2 Microsoft variant version 1
 DEVSD  msmpeg4v2       MPEG-4 part 2 Microsoft variant version 2
 D V D  msrle           Microsoft RLE
 D V D  msvideo1        Microsoft Video 1
 D V D  mszh            LCL (LossLess Codec Library) MSZH
 DEA    nellymoser      Nellymoser Asao
 D V D  nuv             NuppelVideo/RTJPEG
 DEV    pam             PAM (Portable AnyMap) image
 DEV    pbm             PBM (Portable BitMap) image
 DEA    pcm_alaw        PCM A-law
 D A    pcm_dvd         PCM signed 20|24-bit big-endian
 DEA    pcm_f32be       PCM 32-bit floating point big-endian
 DEA    pcm_f32le       PCM 32-bit floating point little-endian
 DEA    pcm_f64be       PCM 64-bit floating point big-endian
 DEA    pcm_f64le       PCM 64-bit floating point little-endian
 DEA    pcm_mulaw       PCM mu-law
 DEA    pcm_s16be       PCM signed 16-bit big-endian
 DEA    pcm_s16le       PCM signed 16-bit little-endian
 D A    pcm_s16le_planar PCM 16-bit little-endian planar
 DEA    pcm_s24be       PCM signed 24-bit big-endian
 DEA    pcm_s24daud     PCM D-Cinema audio signed 24-bit
 DEA    pcm_s24le       PCM signed 24-bit little-endian
 DEA    pcm_s32be       PCM signed 32-bit big-endian
 DEA    pcm_s32le       PCM signed 32-bit little-endian
 DEA    pcm_s8          PCM signed 8-bit
 DEA    pcm_u16be       PCM unsigned 16-bit big-endian
 DEA    pcm_u16le       PCM unsigned 16-bit little-endian
 DEA    pcm_u24be       PCM unsigned 24-bit big-endian
 DEA    pcm_u24le       PCM unsigned 24-bit little-endian
 DEA    pcm_u32be       PCM unsigned 32-bit big-endian
 DEA    pcm_u32le       PCM unsigned 32-bit little-endian
 DEA    pcm_u8          PCM unsigned 8-bit
 DEA    pcm_zork        PCM Zork
 D V    pcx             PC Paintbrush PCX image
 DEV    pgm             PGM (Portable GrayMap) image
 DEV    pgmyuv          PGMYUV (Portable GrayMap YUV) image
 DEV    png             PNG image
 DEV    ppm             PPM (Portable PixelMap) image
 D V    ptx             V.Flash PTX image
 D A    qcelp           QCELP / PureVoice
 D A    qdm2            QDesign Music Codec 2
 D V D  qdraw           Apple QuickDraw
 D V D  qpeg            Q-team QPEG
 DEV D  qtrle           QuickTime Animation (RLE) video
 DEV    rawvideo        raw video
 D A    real_144        RealAudio 1.0 (14.4K)
 D A    real_288        RealAudio 2.0 (28.8K)
 D V D  rl2             RL2 video
 DEA    roq_dpcm        id RoQ DPCM
 DEV D  roqvideo        id RoQ video
 D V D  rpza            QuickTime video (RPZA)
 DEV D  rv10            RealVideo 1.0
 DEV D  rv20            RealVideo 2.0
 D V D  rv30            RealVideo 3.0
 D V D  rv40            RealVideo 4.0
 DEV    sgi             SGI image
 D A    shorten         Shorten
 D A    smackaud        Smacker audio
 D V    smackvid        Smacker video
 D V D  smc             QuickTime Graphics (SMC)
 DEV    snow            Snow
 D A    sol_dpcm        DPCM Sol
 DEA    sonic           Sonic
  EA    sonicls         Sonic lossless
 D V D  sp5x            Sunplus JPEG (SP5X)
 D V    sunrast         Sun Rasterfile image
 DEV D  svq1            Sorenson Vector Quantizer 1
 D VSD  svq3            Sorenson Vector Quantizer 3
 DEV    targa           Truevision Targa image
 D V    theora          Theora
 D V D  thp             Nintendo Gamecube THP video
 D V D  tiertexseqvideo Tiertex Limited SEQ video
 DEV    tiff            TIFF image
 D V D  truemotion1     Duck TrueMotion 1.0
 D V D  truemotion2     Duck TrueMotion 2.0
 D A    truespeech      DSP Group TrueSpeech
 D A    tta             True Audio (TTA)
 D V    txd             Renderware TXD (TeXture Dictionary) image
 D V D  ultimotion      IBM UltiMotion
 D V    vb              Beam Software VB
 D V    vc1             SMPTE VC-1
 D V D  vcr1            ATI VCR1
 D A    vmdaudio        Sierra VMD audio
 D V D  vmdvideo        Sierra VMD video
 D V    vmnc            VMware Screen Codec / VMware Video
 DEA    vorbis          Vorbis
 D V    vp3             On2 VP3
 D V D  vp5             On2 VP5
 D V D  vp6             On2 VP6
 D V D  vp6a            On2 VP6 (Flash version, with alpha channel)
 D V D  vp6f            On2 VP6 (Flash version)
 D V D  vqavideo        Westwood Studios VQA (Vector Quantized Animation) video
 D A    wavpack         WavPack
 DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V    wmv3            Windows Media Video 9
 D V D  wnv1            Winnov WNV1
 D A    ws_snd1         Westwood Audio (SND1)
 D A    xan_dpcm        DPCM Xan
 D V D  xan_wc3         Wing Commander III / Xan
 D V D  xl              Miro VideoXL
 D S    xsub            XSUB
 DEV D  zlib            LCL (LossLess Codec Library) ZLIB
 DEV    zmbv            Zip Motion Blocks Video

```what should i do?
Thanks

---

### Post by BicyclerBoy on 2011-01-09
You have hidden the ffmpeg version info...& all the important media stream info..

Please post
ffmpeg -i recording.mpg

Because these are dvb-t recordings the files are mpeg2-ts.

The contents can be mpeg4/10-H264AVC this commonly used with LATM_AAC LOAS.

The versions of ffmpeg that compile with libfaad needs to be patched for LATM.
The versions of ffmpeg that do not compile with libfaad may not have LATM unless it is a recent version. 

MythTV has (almost) always worked with LATM.

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-09
Hi
This is output of " ffmpeg -i recording.**m2t**"

```
FFmpeg version 0.5.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264 --enable-nonfree
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep  5 2010 15:27:14, gcc: 4.4.3
[NULL @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[NULL @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]non-existing PPS referenced
[h264 @ 0xa63a7b0]non-existing SPS 0 referenced in buffering period
[h264 @ 0xa63a7b0]B picture before any references, skipping
[h264 @ 0xa63a7b0]decode_slice_header error
[h264 @ 0xa63a7b0]no frame!
[h264 @ 0xa63a7b0]number of reference frames exceeds max (probably corrupt input), discarding one
    Last message repeated 500 times
[h264 @ 0xa63a7b0]mmco: unref short failure
Input #0, mpegts, from 'IRINN-190745.m2t':
  Duration: 00:00:21.96, start: 60830.170711, bitrate: 1679 kb/s
  Program 6 
    Stream #0.0[0x3ee]: Video: h264, yuv420p, 720x576 [PAR 12:11 DAR 15:11], 50 tbr, 90k tbn, 50 tbc
At least one output file must be specified

```

---

### Post by BicyclerBoy on 2011-01-09
The file container is mpeg2-ts with MPEG-4/10 H264 .

The other streams are not reported/can not be reported.
The ffmpeg version is very old.
Add multiverse & universe repos
Install libavformat52-extras
Try ffmpeg again.

Can you run mplayer from terminal with this recorded file ?

Like to see what it reports about streams..

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-09
Hi
This is mplayer output (without errors) (it plays both video and audio prefectly!):
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

Playing IRINN-190745.m2t.
TS file format detected.
VIDEO H264(pid=1006) AUDIO AAC(pid=2006) NO SUBS (yet)!  PROGRAM N. 6
FPS seems to be: 25.000000
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:60831.9 V:60833.6 A-V: -1.658 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 [J VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.36:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0xb5ef39c0]BICUBIC scaler, from yuv420p to rgb24 using MMX2
[swscaler @ 0xb5ef39c0]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xb5ef39c0]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xb5ef39c0]using n-tap MMX scaler for vertical scaling (BGR)
[swscaler @ 0xb5ef39c0]720x576 -> 786x576
VO: [xv] 720x576 => 786x576 Planar YV12 
A:60831.9 V:60833.5 A-V: -1.567 ct: -0.004   2/  2 ??% ??% ??,?% 0 0 [J A:60831.9 V:60833.5 A-V: -1.599 ct: -0.008   3/  3 ??% ??% ??,?% 0 0 [J A:60831.9 V:60833.4 A-V: -1.490 ct: -0.012   4/  4 ??% ??% ??,?% 0 0 [J A:60832.0 V:60833.5 A-V: -1.463 ct: -0.016   5/  5 ??% ??% ??,?% 0 0 [J A:60832.0 V:60833.5 A-V: -1.479 ct: -0.020   6/  6 ??% ??% ??,?% 0 0 [J A:60832.1 V:60833.5 A-V: -1.453 ct: -0.024   7/  7 ??% ??% ??,?% 0 0 [J A:60832.1 V:60833.7 A-V: -1.588 ct: -0.028   8/  8 ??% ??% ??,?% 0 0 [J A:60832.2 V:60833.7 A-V: -1.565 ct: -0.032   9/  9 ??% ??% ??,?% 0 0 [J A:60832.2 V:60833.6 A-V: -1.424 ct: -0.036  10/ 10 ??% ??% ??,?% 0 0 [J A:60832.3 V:60833.7 A-V: -1.396 ct: -0.040  11/ 11 ??% ??% ??,?% 0 0 [J A:60832.3 V:60833.6 A-V: -1.290 ct: -0.044  12/ 12 ??% ??% ??,?% 0 0 [J A:60832.3 V:60833.6 A-V: -1.271 ct: -0.048  13/ 13 ??% ??% ??,?% 0 0 [J A:60832.4 V:60833.7 A-V: -1.284 ct: -0.052  14/ 14 41%  3%  4.0% 0 0 [J A:60832.4 V:60833.7 A-V: -1.254 ct: -0.056  15/ 15 39%  3%  3.7% 0 0 [J A:60832.5 V:60833.9 A-V: -1.399 ct: -0.060  16/ 16 37%  3%  3.4% 0 0 [J A:60832.5 V:60833.9 A-V: -1.373 ct: -0.064  17/ 17 36%  2%  3.2% 0 0 [J A:60832.6 V:60833.8 A-V: -1.216 ct: -0.068  18/ 18 34%  4%  3.0% 0 0 [J A:60832.6 V:60833.8 A-V: -1.212 ct: -0.072  19/ 19 33%  4%  3.3% 0 0 [J A:60832.7 V:60833.8 A-V: -1.098 ct: -0.076  20/ 20 32%  4%  3.1% 0 0 [J A:60832.7 V:60833.8 A-V: -1.078 ct: -0.080  21/ 21 31%  4%  3.0% 0 0 [J A:60832.7 V:60833.8 A-V: -1.094 ct: -0.084  22/ 22 30%  5%  2.8% 0 0 [J A:60832.7 V:60833.9 A-V: -1.165 ct: -0.088  23/ 23 29%  5%  2.9% 0 0 [J A:60832.7 V:60834.0 A-V: -1.299 ct: -0.092  24/ 24 28%  5%  2.8% 0 0 [J A:60832.8 V:60834.1 A-V: -1.281 ct: -0.096  25/ 25 28%  5%  2.7% 0 0 [J A:60832.8 V:60834.0 A-V: -1.135 ct: -0.100  26/ 26 27%  5%  2.6% 0 0 [J A:60832.9 V:60834.0 A-V: -1.112 ct: -0.104  27/ 27 27%  5%  2.5% 0 0 [J A:60833.0 V:60833.9 A-V: -0.900 ct: -0.108  28/ 28 26%  5%  2.7% 0 0 [J A:60833.1 V:60833.9 A-V: -0.880 ct: -0.112  29/ 29 26%  5%  2.6% 0 0 [J A:60833.1 V:60834.0 A-V: -0.896 ct: -0.116  30/ 30 25%  5%  2.5% 0 0 [J A:60833.1 V:60834.0 A-V: -0.875 ct: -0.120  31/ 31 25%  5%  2.4% 0 0 [J A:60833.2 V:60834.2 A-V: -1.009 ct: -0.124  32/ 32 24%  5%  2.5% 0 0 [J A:60833.2 V:60834.2 A-V: -0.990 ct: -0.128  33/ 33 24%  4%  2.4% 0 0 [J A:60833.3 V:60834.1 A-V: -0.841 ct: -0.132  34/ 34 24%  5%  2.4% 0 0 [J A:60833.3 V:60834.1 A-V: -0.824 ct: -0.136  35/ 35 24%  5%  2.3% 0 0 [J A:60833.3 V:60834.1 A-V: -0.746 ct: -0.140  36/ 36 23%  5%  2.5% 0 0 [J A:60833.4 V:60834.1 A-V: -0.723 ct: -0.144  37/ 37 23%  4%  2.4% 0 0 [J A:60833.4 V:60834.2 A-V: -0.741 ct: -0.148  38/ 38 22%  4%  2.3% 0 0 [J A:60833.5 V:60834.2 A-V: -0.714 ct: -0.152  39/ 39 22%  4%  2.3% 0 0 [J A:60833.5 V:60834.4 A-V: -0.852 ct: -0.156  40/ 40 22%  4%  2.5% 0 0 [J A:60833.5 V:60834.4 A-V: -0.831 ct: -0.160  41/ 41 22%  4%  2.4% 0 0 [J A:60833.6 V:60834.3 A-V: -0.683 ct: -0.164  42/ 42 22%  4%  2.4% 0 0 [J A:60833.6 V:60834.3 A-V: -0.662 ct: -0.168  43/ 43 21%  4%  2.3% 0 0 [J A:60833.6 V:60834.2 A-V: -0.595 ct: -0.172  44/ 44 21%  4%  2.4% 0 0 [J A:60833.7 V:60834.3 A-V: -0.571 ct: -0.176  45/ 45 21%  4%  2.4% 0 0 [J 
Exiting... (Quit)
```

I compiled ffmpeg by myself and it's not from repositories!
I will enable those and will reinstall ffmpeg 
but installing "libavformat52-extras" will remove lots of my other packages!
I'm currently installing MythTV

---

### Post by BicyclerBoy on 2011-01-09
I am not sure if mplayer is revealing if there is latm aac.
I don't use it.

VLC 1.0.6 goldeneye works fine with latm aac.
 
Just build a new ffmpeg as yours is old..
see the "fakeoutdoorsman" guides here on the Ubuntu forums..
The later ffmpeg does not use libfaad & has latm support.
Your old version needs patches.

There is the risk that the ffplay command line options have changed.
IMO ffplay is a truly awful thing to use.

Try install ubuntu-restricted-extras...

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-10
Hi
I installed the last ffmpeg according to "fakeoutdoorsman" tutorial
Now this h264 video with aac sound plays but both video and sound are slow motion!
I think I was wrong and kaffeine doesn't use ffplay ! It seems it uses Xine !
as gxine reports this recorded video meta info is :
```
Audio Codec: AAC 2.0 (libfaad)
Audio Format: 6 Channels, 32 bit, 44.1kHz, 54000 bps
Video Codec: h.264/AVC (ffmpeg)
Video Format: 720x576, 25.0 fps, 1.36:1, 0 bps
system layer: MPEG_TS
```when I try playing TV from xine-ui or gxine as kaffeine it just plays video!
"ubuntu-restricted-extras" is already installed!

---

### Post by BicyclerBoy on 2011-01-10
Can you
ffmpeg -i recording_file.extension
& post the output ?

Your recording was created on your PC using the dvb-t card ?
Can you provide a short recording on some internet location ?

With 8.04 your xine libs could be way out of date.

I believe there is a direct upgrade path between LTS releases.

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-10
Hi
This is that output:
```
FFmpeg version SVN-r26292, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan 10 2011 08:49:24 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libmp3lame --enable-libvpx
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 0 /  0.16. 0
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.92. 0 / 52.92. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.72. 0 /  1.72. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS referenced
[h264 @ 0xa632250] non-existing SPS 0 referenced in buffering period
[h264 @ 0xa632250] non-existing PPS 0 referenced
[h264 @ 0xa632250] decode_slice_header error
[h264 @ 0xa632250] no frame!
[h264 @ 0xa632250] mmco: unref short failure
[mpegts @ 0xa62c4c0] max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 50.00 (50/1)
Input #0, mpegts, from 'IRINN-190745.m2t':
  Duration: 00:00:21.96, start: 60830.170711, bitrate: 1679 kb/s
  Program 6 
    Stream #0.0[0x3ee]: Video: h264, yuvj420p, 720x576 [PAR 12:11 DAR 15:11], 59.35 fps, 50 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x7d6](per): Audio: aac_latm, 48000 Hz, 2 channels (FC), s16
At least one output file must be specified
```Yes I recorded it using Kaffeine in my PC from DVB-T (While there was no sound! )
MythTv plays/Records with sound without problem.
Now this recorded file plays with sound on VLC & mplayer properly but ...
It plays slow motion with sound on new ffplay.
It plays without sound in gxine, xine-ui and Kaffeine!
I think the problem is in xine engine!

OK I will try find a recording from internet. (but Kaffeine and other xine based players play other formats without problem and just this one has problem)

I'm not on 8.04! my profile was out of date!! I'm currently on 10.04 (Lucid Lynx)

---

### Post by BicyclerBoy on 2011-01-10
Hurray

The new ffmpeg reveals latm_aac.

i think your system search path is finding an old ffplay not your new build executable.
Ffmpeg recommend using ffmpeg -i or ffprobe to probe the media.

which ffplay

Where did you install the new ffmpeg packages ?

Latm_aac is only (commonly?) used in transport streams like broadcast TV.
You may not come across it anywhere else.

It my part of the world, dvb-t  has been using latm_aac from the start.
It is quickly becoming more widespread thru'-out Europe.

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-10
Hi
No, ffplay has the same version as ffmpeg:
```
FFplay version SVN-r26292, Copyright (c) 2003-2011 the FFmpeg developers
```none of "ffmpeg -i" & ffprobe play video!

which ffplay:
```
/usr/local/bin/ffplay
```which ffmpeg:
```
/usr/local/bin/ffmpeg
```new ffplay plays both video & sound but both are slow motion!

Do you think xine problem is beacuase of ffmpeg?

---

### Post by BicyclerBoy on 2011-01-10
I know they don't play..
I was only interested in the stream & codec information..
ffplay is not reliable..

I believe xine is using ffmpeg's libraries libav* (old & patched) & w32-codecs (don't know where they come from).

AFAIK There are (2) fundamental projects that provide universal transcoding/codecs
ffmpeg & gstreamer.

Xine does not work because your xine libs do not support latm_aac.
You need to check the Xine forums.

The solution depends on whether your application is built with static libraries or shared dynamic system libraries.
Check this in synaptic package properties/dependencies.
The system libraries are the (~7) libav*-unstripped from universe multiverse medibunti?

Ubuntu repos managed packages tend to use system libs.

DIY stuff tends to use static (private).

If MythTV works what more could you possibly want ?
XBMC as frontend maybe ?

---

### Post by BicyclerBoy on 2011-01-12
Snigger ?

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-12
Hi
Excuse me! 
Where you found out "Snigger"? decoded username or you know me from somewhere else?:?::D
I installed xine from repositories.
"libavcodec-unstriped-52" , "libavdevice-unstriped-52" ,"libavutil-unstriped-49" , "libavformat-unstriped-52" are installed and "libavfilter-unstriped-0" is not installed.
none of libxine* & gxine & xine-ui  depends on libav*  (if i understood you correctly)!

The problem with MythTv is its shortcuts complexity!
No problem , I'll use mythTv but when I play mythTv's recordings with mplayer video is slow motion!! (Audio is OK! while in MythTv itself both are OK!!).

---

### Post by BicyclerBoy on 2011-01-12
"\x44\x65\x63\x6f\x64\x65\x64\x2e"

You could try build xine from source. It should include a private copy of the contributing projects used.

There are patches for ffmpeg (using libfaad) in handbrake & mythtv projects.

The latest ffmpeg has internal aac decode & latm support.
If xine will compile with the latest ffmpeg (libav*) then latm aac will be supported.

I don't use mplayer..but maybe this needs to be built from source as well.

---

### Post by no2498 on 2011-01-12
try installing smplayer just for my piece of mind i think it helps with mp4 files
some say im crazy 
type it in a terminal it tells you how to install it
just for me please

---

### Post by BicyclerBoy on 2011-01-12
He has a (best IMHO) working player in MythTV.

The issue is how to get xine libxine supporting latm_aac.

I'm very sure that a DIY build or 3rd party ppa of mplayer will work.
mplayer is the hosting website of ffmpeg.

VLC has worked with latm_aac for as long as I can remember.

---

