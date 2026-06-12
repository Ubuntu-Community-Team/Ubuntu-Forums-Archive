---
title: "Rendering as H264 in Kdenlive"
date: 2013-01-03
forum: Multimedia Software
---

### Post by GrouchyGaijin on 2013-01-03
Hi Folks,

I've noticed that if I try to render a video using H264 in kdenlive I end up with a file that has no video but does have sound.

Remdering as mpeg4 which also seems to use the same mp4 container works fine.

I **don't get any** error message from kdenlive such as no video codec installed, so I don't really know why I'm having this problem.

Any help would be much appreciated.

[IMG]https://dl.dropbox.com/u/23115609/Screenshot%20from%202013-01-03%2012%3A57%3A04.png[/IMG]

---

### Post by GrouchyGaijin on 2013-01-03
Hi Folks,

I have an ffmpeg command that I've been using to convert videos into flash video.

```
ffmpeg -i foo1.avi -b 400000 -s qvga -acodec libmp3lame -ar 22050 bar.flv
```

I'd like to create a rendering profile in kdenlive that uses these same settings.

I'm having trouble putting the following settings into kdenlive.
```
-b 400000 -s qvga -acodec libmp3lame -ar 22050
```

I've tried several variations of the following:
```
f=flv acodec=libmp3lame ar=22050 vcodec=flv minrate=0 vb=400000k s=320x240
```

I keep getting the following error when I try to play a video that has been rendered using the profile I created.

[COLOR="Red"]No suitable decoder module:
VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/COLOR]

Does anyone know how I can solve this problem?  I'd really appreciate the help.

---

### Post by FakeOutdoorsman on 2013-01-03
I'll guess that either the Kdenlive presets use old syntax and/or your ffmpeg doesn't have libx264 support enabled. Make sure you have **libavcodec-extra-5*** installed if you're using "ffmpeg" from the repo. It will enable additional encoders that, annoyingly, Ubuntu did not enable by default.

---

### Post by GrouchyGaijin on 2013-01-03
> **FakeOutdoorsman said:**
> I'll guess that either the Kdenlive presets use old syntax and/or your ffmpeg doesn't have libx264 support enabled. Make sure you have **libavcodec-extra-5*** installed if you're using "ffmpeg" from the repo. It will enable additional encoders that, annoyingly, Ubuntu did not enable by default.

Hi,

Thank you for the reply.

Actually, I'm using the dev version of ffmpeg.
```
ffmpeg version git-2013-01-02-e4f14c3 Copyright (c) 2000-2013 the FFmpeg developers
  built on Jan  2 2013 18:16:31 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 13.100 / 52. 13.100
  libavcodec     54. 85.100 / 54. 85.100
  libavformat    54. 59.100 / 54. 59.100
  libavdevice    54.  3.102 / 54.  3.102
  libavfilter     3. 30.102 /  3. 30.102
  libswscale      2.  1.103 /  2.  1.103
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100

```
I installed it by following the guide here:
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")

The ffmpeg -formats command brings up these:
```
File formats:
 D. = Demuxing supported
 .E = Muxing supported
 --
  E 3g2             3GP2 (3GPP2 file format)
  E 3gp             3GP (3GPP file format)
 D  4xm             4X Technologies
  E a64             a64 - video for Commodore 64
 D  aac             raw ADTS AAC (Advanced Audio Coding)
 DE ac3             raw AC-3
 D  act             ACT Voice file format
 D  adf             Artworx Data Format
  E adts            ADTS AAC (Advanced Audio Coding)
 DE adx             CRI ADX
 D  aea             MD STUDIO audio
 D  afc             AFC
 DE aiff            Audio IFF
 DE alaw            PCM A-law
 DE alsa            ALSA audio output
 DE amr             3GPP AMR
 D  anm             Deluxe Paint Animation
 D  apc             CRYO APC
 D  ape             Monkey's Audio
 D  aqtitle         AQTitle subtitles
 DE asf             ASF (Advanced / Active Streaming Format)
  E asf_stream      ASF (Advanced / Active Streaming Format)
 DE ***             SSA (SubStation Alpha) subtitle
 DE ast             AST (Audio Stream)
 DE au              Sun AU
 DE avi             AVI (Audio Video Interleaved)
  E avm2            SWF (ShockWave Flash) (AVM2)
 D  avr             AVR (Audio Visual Research)
 D  avs             AVS
 D  bethsoftvid     Bethesda Softworks VID
 D  bfi             Brute Force & Ignorance
 D  bin             Binary text
 D  bink            Bink
 DE bit             G.729 BIT file format
 D  bmv             Discworld II BMV
 D  brstm           BRSTM (Binary Revolution Stream)
 D  c93             Interplay C93
 DE caf             Apple CAF (Core Audio Format)
 DE cavsvideo       raw Chinese AVS (Audio Video Standard) video
 D  cdg             CD Graphics
 D  cdxl            Commodore CDXL video
 D  concat          Virtual concatenation script
  E crc             CRC testing
 DE daud            D-Cinema audio
 D  dfa             Chronomaster DFA
 DE dirac           raw Dirac
 DE dnxhd           raw DNxHD (SMPTE VC-3)
 D  dsicin          Delphine Software International CIN
 DE dts             raw DTS
 D  dtshd           raw DTS-HD
 DE dv              DV (Digital Video)
 D  dv1394          DV1394 A/V grab
  E dvd             MPEG-2 PS (DVD VOB)
 D  dxa             DXA
 D  ea              Electronic Arts Multimedia
 D  ea_cdata        Electronic Arts cdata
 DE eac3            raw E-AC-3
 D  epaf            Ensoniq Paris Audio File
 DE f32be           PCM 32-bit floating-point big-endian
 DE f32le           PCM 32-bit floating-point little-endian
  E f4v             F4V Adobe Flash Video
 DE f64be           PCM 64-bit floating-point big-endian
 DE f64le           PCM 64-bit floating-point little-endian
 D  fbdev           Linux framebuffer
 DE ffm             FFM (FFserver live feed)
 DE ffmetadata      FFmpeg metadata in text
 D  film_cpk        Sega FILM / CPK
 DE filmstrip       Adobe Filmstrip
 DE flac            raw FLAC
 D  flic            FLI/FLC/FLX animation
 DE flv             FLV (Flash Video)
  E framecrc        framecrc testing
  E framemd5        Per-frame MD5 testing
 DE g722            raw G.722
 DE g723_1          raw G.723.1
 D  g729            G.729 raw format demuxer
 DE gif             GIF Animation
 D  gsm             raw GSM
 DE gxf             GXF (General eXchange Format)
 DE h261            raw H.261
 DE h263            raw H.263
 DE h264            raw H.264 video
  E hls             Apple HTTP Live Streaming
 D  hls,applehttp   Apple HTTP Live Streaming
 DE ico             Microsoft Windows ICO
 D  idcin           id Cinematic
 D  idf             iCE Draw File
 D  iff             IFF (Interchange File Format)
 DE ilbc            iLBC storage
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       raw Ingenient MJPEG
 D  ipmovie         Interplay MVE
  E ipod            iPod H.264 MP4 (MPEG-4 Part 14)
 DE ircam           Berkeley/IRCAM/CARL Sound Format
  E ismv            ISMV/ISMA (Smooth Streaming)
 D  iss             Funcom ISS
 D  iv8             IndigoVision 8000 video
 DE ivf             On2 IVF
 D  jack            JACK Audio Connection Kit
 DE jacosub         JACOsub subtitle format
 D  jv              Bitmap Brothers JV
 DE latm            LOAS/LATM
 D  lavfi           Libavfilter virtual input device
 D  lmlm4           raw lmlm4
 D  loas            LOAS AudioSyncStream
 D  lvf             LVF
 D  lxf             VR native stream (LXF)
 DE m4v             raw MPEG-4 video
  E matroska        Matroska
 D  matroska,webm   Matroska / WebM
  E md5             MD5 testing
 D  mgsts           Metal Gear Solid: The Twin Snakes
 DE microdvd        MicroDVD subtitle format
 DE mjpeg           raw MJPEG video
  E mkvtimestamp_v2 extract pts as timecode v2 format, as defined by mkvtoolnix
 DE mlp             raw MLP
 D  mm              American Laser Games MM
 DE mmf             Yamaha SMAF
  E mov             QuickTime / MOV
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime / MOV
  E mp2             MP2 (MPEG audio layer 2)
 DE mp3             MP3 (MPEG audio layer 3)
  E mp4             MP4 (MPEG-4 Part 14)
 D  mpc             Musepack
 D  mpc8            Musepack SV8
 DE mpeg            MPEG-1 Systems / MPEG program stream
  E mpeg1video      raw MPEG-1 video
  E mpeg2video      raw MPEG-2 video
 DE mpegts          MPEG-TS (MPEG-2 Transport Stream)
 D  mpegtsraw       raw MPEG-TS (MPEG-2 Transport Stream)
 D  mpegvideo       raw MPEG video
  E mpjpeg          MIME multipart JPEG
 D  mpl2            MPL2 subtitles
 D  mpsub           MPlayer subtitles
 D  msnwctcp        MSN TCP Webcam stream
 D  mtv             MTV
 DE mulaw           PCM mu-law
 D  mv              Silicon Graphics Movie
 D  mvi             Motion Pixels MVI
 DE mxf             MXF (Material eXchange Format)
  E mxf_d10         MXF (Material eXchange Format) D-10 Mapping
 D  mxg             MxPEG clip
 D  nc              NC camera feed
 D  nistsphere      NIST SPeech HEader REsources
 D  nsv             Nullsoft Streaming Video
  E null            raw null video
 DE nut             NUT
 D  nuv             NuppelVideo
 DE ogg             Ogg
 DE oma             Sony OpenMG audio
 DE oss             OSS (Open Sound System) playback
 D  paf             Amazing Studio Packed Animation File
 D  pjs             PJS (Phoenix Japanimation Society) subtitles
 D  pmp             Playstation Portable PMP
  E psp             PSP MP4 (MPEG-4 Part 14)
 D  psxstr          Sony Playstation STR
 D  pva             TechnoTrend PVA
 D  pvf             PVF (Portable Voice Format)
 D  qcp             QCP
 D  r3d             REDCODE R3D
 DE rawvideo        raw video
  E rcv             VC-1 test bitstream
 D  realtext        RealText subtitle format
 D  rl2             RL2
 DE rm              RealMedia
 DE roq             raw id RoQ
 D  rpl             RPL / ARMovie
 DE rso             Lego Mindstorms RSO
 DE rtp             RTP output
 DE rtsp            RTSP output
 DE s16be           PCM signed 16-bit big-endian
 DE s16le           PCM signed 16-bit little-endian
 DE s24be           PCM signed 24-bit big-endian
 DE s24le           PCM signed 24-bit little-endian
 DE s32be           PCM signed 32-bit big-endian
 DE s32le           PCM signed 32-bit little-endian
 DE s8              PCM signed 8-bit
 D  sami            SAMI subtitle format
 DE sap             SAP output
 D  sbg             SBaGen binaural beats script
  E sdl             SDL output device
 D  sdp             SDP
  E segment         segment
 D  shn             raw Shorten
 D  siff            Beam Software SIFF
 DE smjpeg          Loki SDL MJPEG
 D  smk             Smacker
  E smoothstreaming Smooth Streaming Muxer
 D  smush           LucasArts Smush
 D  sol             Sierra SOL
 DE sox             SoX native
 DE spdif           IEC 61937 (used on S/PDIF - IEC958)
 DE srt             SubRip subtitle
  E stream_segment,ssegment streaming segment muxer
 D  subviewer       SubViewer subtitle format
 D  subviewer1      SubViewer v1 subtitle format
  E svcd            MPEG-2 PS (SVCD)
 DE swf             SWF (ShockWave Flash)
 D  tak             raw TAK
 D  tedcaptions     TED Talks captions
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ
 D  tmv             8088flex TMV
 DE truehd          raw TrueHD
 D  tta             TTA (True Audio)
 D  tty             Tele-typewriter
 D  txd             Renderware TeXture Dictionary
 DE u16be           PCM unsigned 16-bit big-endian
 DE u16le           PCM unsigned 16-bit little-endian
 DE u24be           PCM unsigned 24-bit big-endian
 DE u24le           PCM unsigned 24-bit little-endian
 DE u32be           PCM unsigned 32-bit big-endian
 DE u32le           PCM unsigned 32-bit little-endian
 DE u8              PCM unsigned 8-bit
 D  vc1             raw VC-1
 D  vc1test         VC-1 test bitstream
  E vcd             MPEG-1 Systems / MPEG program stream (VCD)
 D  video4linux2,v4l2 Video4Linux2 device grab
 D  vivo            Vivo
 D  vmd             Sierra VMD
  E vob             MPEG-2 PS (VOB)
 D  vobsub          VobSub subtitle format
 DE voc             Creative Voice
 D  vplayer         VPlayer subtitles
 D  vqf             Nippon Telegraph and Telephone Corporation (NTT) TwinVQ
 DE w64             Sony Wave64
 DE wav             WAV / WAVE (Waveform Audio)
 D  wc3movie        Wing Commander III movie
  E webm            WebM
 D  webvtt          WebVTT subtitle
 D  wsaud           Westwood Studios audio
 D  wsvqa           Westwood Studios VQA
 DE wtv             Windows Television (WTV)
 DE wv              WavPack
 D  x11grab         X11grab
 D  xa              Maxis XA
 D  xbin            eXtended BINary text (XBIN)
 D  xmv             Microsoft XMV
 D  xwma            Microsoft xWMA
 D  yop             Psygnosis YOP
 DE yuv4mpegpipe    YUV4MPEG pipe

```

Can you tell if I am missing the ones you had in mind?

---

### Post by dannyboy79 on 2013-01-03
i am using kdenlive from sunab's kdenlive-release ppa and using ffmpeg from medibuntu repositories I believe and can render to h264 using mp4 container

---

### Post by GrouchyGaijin on 2013-01-08
I stopped using the video codec flv and started using libx264.  Now it works.

---

### Post by GrouchyGaijin on 2013-01-08
The problem seems to be fixed if I change the video codec from flv to libx264 in kden's render profile.

---

### Post by mörgæs on 2013-01-08
Threads merged.
Please don't double-post.

---

