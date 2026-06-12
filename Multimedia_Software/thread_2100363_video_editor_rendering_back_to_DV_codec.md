---
title: "video editor rendering back to DV codec?"
date: 2013-01-01
forum: Multimedia Software
---

### Post by sdowney717 on 2013-01-01
Any editors besides cinelerra?

I found cinelerra can render back to DV codec. BUT it CRASHES frequently to the point I dont think I can use it. They say just load backup which will work. My crash happened on a file overwrite. then the movie was destroyed and now have to recapture it.:evil:

SO, I would like someone to tell me if there is another editor can render to DV codec. The advantage is keeping the same quality on your captures and very quick to render DV.

---

### Post by sdowney717 on 2013-01-01
I found that kdenlive can render back to dv video.

I was running flowblade and you can render to arguments. Does anyone have arguments that I can test?

from avconf -codecs, I see a codec called dvvideo

```
scott@scott-P5QC:~$ avconv
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3
Hyper fast Audio and Video encoder
usage: avconv [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man avconv'
scott@scott-P5QC:~$ avconv -codecs
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3
Codecs:
 D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec
 ..S... = Subtitle codec
 ...S.. = Supports draw_horiz_band
 ....D. = Supports direct rendering method 1
 .....T = Supports weird frame truncation
 ------
 D V D  4xm             4X Movie
 D V D  8bps            QuickTime 8BPS video
 D A D  8svx_exp        8SVX exponential
 D A D  8svx_fib        8SVX fibonacci
 D V D  FRWU            Forward Uncompressed
  EV    a64multi        Multicolor charset for Commodore 64
  EV    a64multi5       Multicolor charset for Commodore 64, extended with 5th color (colram)
 DEA D  aac             Advanced Audio Coding
 D A D  aac_latm        AAC LATM (Advanced Audio Codec LATM syntax)
 D V D  aasc            Autodesk RLE
 DEA D  ac3             ATSC A/52A (AC-3)
  EA    ac3_fixed       ATSC A/52A (AC-3)
 D A D  adpcm_4xm       ADPCM 4X Movie
 DEA D  adpcm_adx       SEGA CRI ADX ADPCM
 D A D  adpcm_ct        ADPCM Creative Technology
 D A D  adpcm_ea        ADPCM Electronic Arts
 D A D  adpcm_ea_maxis_xa ADPCM Electronic Arts Maxis CDROM XA
 D A D  adpcm_ea_r1     ADPCM Electronic Arts R1
 D A D  adpcm_ea_r2     ADPCM Electronic Arts R2
 D A D  adpcm_ea_r3     ADPCM Electronic Arts R3
 D A D  adpcm_ea_xas    ADPCM Electronic Arts XAS
 D A D  adpcm_ima_amv   ADPCM IMA AMV
 D A D  adpcm_ima_dk3   ADPCM IMA Duck DK3
 D A D  adpcm_ima_dk4   ADPCM IMA Duck DK4
 D A D  adpcm_ima_ea_eacs ADPCM IMA Electronic Arts EACS
 D A D  adpcm_ima_ea_sead ADPCM IMA Electronic Arts SEAD
 D A D  adpcm_ima_iss   ADPCM IMA Funcom ISS
 DEA D  adpcm_ima_qt    ADPCM IMA QuickTime
 D A D  adpcm_ima_smjpeg ADPCM IMA Loki SDL MJPEG
 DEA D  adpcm_ima_wav   ADPCM IMA WAV
 D A D  adpcm_ima_ws    ADPCM IMA Westwood
 DEA D  adpcm_ms        ADPCM Microsoft
 D A D  adpcm_sbpro_2   ADPCM Sound Blaster Pro 2-bit
 D A D  adpcm_sbpro_3   ADPCM Sound Blaster Pro 2.6-bit
 D A D  adpcm_sbpro_4   ADPCM Sound Blaster Pro 4-bit
 DEA D  adpcm_swf       ADPCM Shockwave Flash
 D A D  adpcm_thp       ADPCM Nintendo Gamecube THP
 D A D  adpcm_xa        ADPCM CDROM XA
 DEA D  adpcm_yamaha    ADPCM Yamaha
 DEA D  alac            ALAC (Apple Lossless Audio Codec)
 D A D  als             MPEG-4 Audio Lossless Coding (ALS)
 D A D  amrnb           Adaptive Multi-Rate NarrowBand
 D A D  amrwb           Adaptive Multi-Rate WideBand
 D V    amv             AMV Video
 D V D  anm             Deluxe Paint Animation
 D V D  ansi            ASCII/ANSI art
 D A D  ape             Monkey's Audio
 DES    ***             Advanced SubStation Alpha subtitle
 DEV D  asv1            ASUS V1
 DEV D  asv2            ASUS V2
 D A D  atrac1          Atrac 1 (Adaptive TRansform Acoustic Coding)
 D A D  atrac3          Atrac 3 (Adaptive TRansform Acoustic Coding 3)
 D V D  aura            Auravision AURA
 D V D  aura2           Auravision Aura 2
 D V D  avs             AVS (Audio Video Standard) video
 D V D  bethsoftvid     Bethesda VID video
 D V D  bfi             Brute Force & Ignorance
 D A D  binkaudio_dct   Bink Audio (DCT)
 D A D  binkaudio_rdft  Bink Audio (RDFT)
 D V    binkvideo       Bink video
 DEV D  bmp             BMP image
 D A D  bmv_audio       Discworld II BMV audio
 D V    bmv_video       Discworld II BMV video
 D V D  c93             Interplay C93
 D V D  camstudio       CamStudio
 D V D  camtasia        TechSmith Screen Capture Codec
 D V D  cavs            Chinese AVS video (AVS1-P2, JiZhun profile)
 D V D  cdgraphics      CD Graphics video
 D V D  cinepak         Cinepak
 DEV D  cljr            Cirrus Logic AccuPak
 D A D  cook            COOK
 D V D  cyuv            Creative YUV (CYUV)
 D A D  dca             DCA (DTS Coherent Acoustics)
 D V D  dfa             Chronomaster DFA
 DEV D  dnxhd           VC3/DNxHD
 DEV    dpx             DPX image
 D A D  dsicinaudio     Delphine Software International CIN audio
 D V D  dsicinvideo     Delphine Software International CIN video
 DES    dvbsub          DVB subtitles
 DES    dvdsub          DVD subtitles
 DEV D  dvvideo         DV (Digital Video)
 D V D  dxa             Feeble Files/ScummVM DXA
 D V D  dxtory          Dxtory
 DEA D  eac3            ATSC A/52 E-AC-3
 D V D  eacmv           Electronic Arts CMV video
 D V D  eamad           Electronic Arts Madcow Video
 D V D  eatgq           Electronic Arts TGQ video
 D V    eatgv           Electronic Arts TGV video
 D V D  eatqi           Electronic Arts TQI Video
 D V D  escape124       Escape 124
 DEV D  ffv1            FFmpeg video codec #1
 DEVSD  ffvhuff         Huffyuv FFmpeg variant
 DEA D  flac            FLAC (Free Lossless Audio Codec)
 DEV D  flashsv         Flash Screen Video
 D V D  flashsv2        Flash Screen Video v2
 D V D  flic            Autodesk Animator Flic video
 DEVSD  flv             Flash Video (FLV) / Sorenson Spark / Sorenson H.263
 D V D  fraps           Fraps
 DEA D  g722            G.722 ADPCM
 DEA D  g726            G.726 ADPCM
 DEV D  gif             GIF (Graphics Interchange Format)
 D A D  gsm             GSM
 D A D  gsm_ms          GSM Microsoft variant
 DEV D  h261            H.261
 DEVSDT h263            H.263 / H.263-1996
 D VSD  h263i           Intel H.263
  EV    h263p           H.263+ / H.263-1998 / H.263 version 2
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 DEVSD  huffyuv         Huffyuv / HuffYUV
 D V D  idcinvideo      id Quake II CIN video
 D V D  iff_byterun1    IFF ByteRun1
 D V D  iff_ilbm        IFF ILBM
 D A D  imc             IMC (Intel Music Coder)
 D V D  indeo2          Intel Indeo 2
 D V    indeo3          Intel Indeo 3
 D V    indeo4          Intel Indeo Video Interactive 4
 D V    indeo5          Intel Indeo Video Interactive 5
 D A D  interplay_dpcm  DPCM Interplay
 D V D  interplayvideo  Interplay MVE video
 DEV D  jpegls          JPEG-LS
 D V D  jv              Bitmap Brothers JV video
 D V    kgv1            Kega Game Video
 D V D  kmvc            Karl Morton's video codec
 D V D  lagarith        Lagarith lossless
  EV    libdirac        libdirac Dirac 2.2
 DEA D  libgsm          libgsm GSM
 DEA D  libgsm_ms       libgsm GSM Microsoft variant
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
 D V D  libopenjpeg     OpenJPEG based JPEG 2000 decoder
 DEV    libschroedinger libschroedinger Dirac 2.2
 DEA D  libspeex        libspeex Speex
  EV    libtheora       libtheora Theora
  EA    libvo_aacenc    Android VisualOn AAC
  EA    libvo_amrwbenc  Android VisualOn Adaptive Multi-Rate (AMR) Wide-Band
  EA    libvorbis       libvorbis Vorbis
 DEV    libvpx          libvpx VP8
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EV    libxvid         libxvidcore MPEG-4 part 2
  EV    ljpeg           Lossless JPEG
 D V D  loco            LOCO
 D A D  mace3           MACE (Macintosh Audio Compression/Expansion) 3:1
 D A D  mace6           MACE (Macintosh Audio Compression/Expansion) 6:1
 D V D  mdec            Sony PlayStation MDEC (Motion DECoder)
 D V D  mimic           Mimic
 DEV D  mjpeg           MJPEG (Motion JPEG)
 D V D  mjpegb          Apple MJPEG-B
 D A D  mlp             MLP (Meridian Lossless Packing)
 D V D  mmvideo         American Laser Games MM Video
 D V D  motionpixels    Motion Pixels video
 D A D  mp1             MP1 (MPEG audio layer 1)
 D A D  mp1float        MP1 (MPEG audio layer 1)
 DEA D  mp2             MP2 (MPEG audio layer 2)
 D A D  mp2float        MP2 (MPEG audio layer 2)
 D A D  mp3             MP3 (MPEG audio layer 3)
 D A D  mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A D  mp3adufloat     ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A D  mp3float        MP3 (MPEG audio layer 3)
 D A D  mp3on4          MP3onMP4
 D A D  mp3on4float     MP3onMP4
 D A D  mpc7            Musepack SV7
 D A D  mpc8            Musepack SV8
 DEVSDT mpeg1video      MPEG-1 video
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 DEVSDT mpeg2video      MPEG-2 video
 DEVSDT mpeg4           MPEG-4 part 2
 D V DT mpeg4_vdpau     MPEG-4 part 2 (VDPAU)
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D VSDT mpegvideo_xvmc  MPEG-1/2 video XvMC (X-Video Motion Compensation)
 DEVSD  msmpeg4         MPEG-4 part 2 Microsoft variant version 3
 D VSD  msmpeg4v1       MPEG-4 part 2 Microsoft variant version 1
 DEVSD  msmpeg4v2       MPEG-4 part 2 Microsoft variant version 2
 D V D  msrle           Microsoft RLE
 D V D  msvideo1        Microsoft Video 1
 D V D  mszh            LCL (LossLess Codec Library) MSZH
 D V D  mxpeg           Mobotix MxPEG video
 DEA D  nellymoser      Nellymoser Asao
 D V D  nuv             NuppelVideo/RTJPEG
 DEV D  pam             PAM (Portable AnyMap) image
 DEV D  pbm             PBM (Portable BitMap) image
 D A D  pcm_alaw        PCM A-law
 D A D  pcm_bluray      PCM signed 16|20|24-bit big-endian for Blu-ray media
 D A D  pcm_dvd         PCM signed 20|24-bit big-endian
 D A D  pcm_f32be       PCM 32-bit floating point big-endian
 D A D  pcm_f32le       PCM 32-bit floating point little-endian
 D A D  pcm_f64be       PCM 64-bit floating point big-endian
 D A D  pcm_f64le       PCM 64-bit floating point little-endian
 D A D  pcm_lxf         PCM signed 20-bit little-endian planar
 D A D  pcm_mulaw       PCM mu-law
 D A D  pcm_s16be       PCM signed 16-bit big-endian
 D A D  pcm_s16le       PCM signed 16-bit little-endian
 D A D  pcm_s16le_planar PCM 16-bit little-endian planar
 D A D  pcm_s24be       PCM signed 24-bit big-endian
 D A D  pcm_s24daud     PCM D-Cinema audio signed 24-bit
 D A D  pcm_s24le       PCM signed 24-bit little-endian
 D A D  pcm_s32be       PCM signed 32-bit big-endian
 D A D  pcm_s32le       PCM signed 32-bit little-endian
 D A D  pcm_s8          PCM signed 8-bit
 D A D  pcm_s8_planar   PCM signed 8-bit planar
 D A D  pcm_u16be       PCM unsigned 16-bit big-endian
 D A D  pcm_u16le       PCM unsigned 16-bit little-endian
 D A D  pcm_u24be       PCM unsigned 24-bit big-endian
 D A D  pcm_u24le       PCM unsigned 24-bit little-endian
 D A D  pcm_u32be       PCM unsigned 32-bit big-endian
 D A D  pcm_u32le       PCM unsigned 32-bit little-endian
 D A D  pcm_u8          PCM unsigned 8-bit
 D A D  pcm_zork        PCM Zork
 DEV D  pcx             PC Paintbrush PCX image
 DEV D  pgm             PGM (Portable GrayMap) image
 DEV D  pgmyuv          PGMYUV (Portable GrayMap YUV) image
 D S    pgssub          HDMV Presentation Graphic Stream subtitles
 D V D  pictor          Pictor/PC Paint
 DEV D  png             PNG image
 DEV D  ppm             PPM (Portable PixelMap) image
 D V D  prores          Apple ProRes (iCodec Pro)
 D V D  ptx             V.Flash PTX image
 D A D  qcelp           QCELP / PureVoice
 D A D  qdm2            QDesign Music Codec 2
 D V D  qdraw           Apple QuickDraw
 D V D  qpeg            Q-team QPEG
 DEV D  qtrle           QuickTime Animation (RLE) video
 D V D  r10k            AJA Kona 10-bit RGB Codec
 D V D  r210            Uncompressed RGB 10-bit
 DEV    rawvideo        raw video
 DEA D  real_144        RealAudio 1.0 (14.4K) encoder
 D A D  real_288        RealAudio 2.0 (28.8K)
 D V D  rl2             RL2 video
 DEA D  roq_dpcm        id RoQ DPCM
 DEV D  roqvideo        id RoQ video
 D V D  rpza            QuickTime video (RPZA)
 DEV D  rv10            RealVideo 1.0
 DEV D  rv20            RealVideo 2.0
 D V D  rv30            RealVideo 3.0
 D V D  rv40            RealVideo 4.0
 D A D  s302m           SMPTE 302M
 DEV    sgi             SGI image
 D A D  shorten         Shorten
 D A D  sipr            RealAudio SIPR / ACELP.NET
 D A D  smackaud        Smacker audio
 D V D  smackvid        Smacker video
 D V D  smc             QuickTime Graphics (SMC)
 DEV D  snow            Snow
 D A D  sol_dpcm        DPCM Sol
 D V D  sp5x            Sunplus JPEG (SP5X)
 D S    srt             SubRip subtitle
 D V D  sunrast         Sun Rasterfile image
 DEV D  svq1            Sorenson Vector Quantizer 1 / Sorenson Video 1 / SVQ1
 D VSD  svq3            Sorenson Vector Quantizer 3 / Sorenson Video 3 / SVQ3
 DEV D  targa           Truevision Targa image
 D VSD  theora          Theora
 D V D  thp             Nintendo Gamecube THP video
 D V D  tiertexseqvideo Tiertex Limited SEQ video
 DEV D  tiff            TIFF image
 D V D  tmv             8088flex TMV
 D A D  truehd          TrueHD
 D V D  truemotion1     Duck TrueMotion 1.0
 D V D  truemotion2     Duck TrueMotion 2.0
 D A D  truespeech      DSP Group TrueSpeech
 D A D  tta             True Audio (TTA)
 D A D  twinvq          VQF TwinVQ
 D V D  txd             Renderware TXD (TeXture Dictionary) image
 D V D  ultimotion      IBM UltiMotion
 D V D  utvideo         Ut Video
 DEV D  v210            Uncompressed 4:2:2 10-bit
 D V D  v210x           Uncompressed 4:2:2 10-bit
 DEV D  v410            Uncompressed 4:4:4 10-bit
 D V    vb              Beam Software VB
 D V D  vble            VBLE Lossless Codec
 D V D  vc1             SMPTE VC-1
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  vc1image        Windows Media Video 9 Image v2
 D V D  vcr1            ATI VCR1
 D A D  vmdaudio        Sierra VMD audio
 D V D  vmdvideo        Sierra VMD video
 D V D  vmnc            VMware Screen Codec / VMware Video
 DEA D  vorbis          Vorbis
 D VSD  vp3             On2 VP3
 D V D  vp5             On2 VP5
 D V D  vp6             On2 VP6
 D V D  vp6a            On2 VP6 (Flash version, with alpha channel)
 D V D  vp6f            On2 VP6 (Flash version)
 D V D  vp8             On2 VP8
 D V D  vqavideo        Westwood Studios VQA (Vector Quantized Animation) video
 D A D  wavpack         WavPack
 D A D  wmapro          Windows Media Audio 9 Professional
 DEA D  wmav1           Windows Media Audio 1
 DEA D  wmav2           Windows Media Audio 2
 D A D  wmavoice        Windows Media Audio Voice
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V D  wmv3            Windows Media Video 9
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU
 D V D  wmv3image       Windows Media Video 9 Image
 D V D  wnv1            Winnov WNV1
 D A D  ws_snd1         Westwood Audio (SND1)
 D A D  xan_dpcm        DPCM Xan
 D V D  xan_wc3         Wing Commander III / Xan
 D V D  xan_wc4         Wing Commander IV / Xxan
 D V D  xl              Miro VideoXL
 DES    xsub            DivX subtitles (XSUB)
 D V    yop             Psygnosis YOP Video
 DEV D  zlib            LCL (LossLess Codec Library) ZLIB
 DEV D  zmbv            Zip Motion Blocks Video

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.
scott@scott-P5QC:~$ 

```


this is one of the preset mpeg2
```
f=mpeg
acodec=mp2
ab=384k
ar=48000
vcodec=mpeg2video
minrate=0
vb=3000k
bf=2
b_strategy=1
trellis=1
```

I think if i had the arguments right, then flowblade could do it

---

### Post by FakeOutdoorsman on 2013-01-01
Example ffmpeg commands that you can turn into various presets in your editor:
```
ffmpeg -i input -target ntsc-dv output.dv
```
or
```
ffmpeg -i input -target pal-dv output.dv
```
Depending if you're working with NTSC or PAL inputs.

---

