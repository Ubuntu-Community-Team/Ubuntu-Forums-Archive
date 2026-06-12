---
title: "VLC doesn't play V_AV1 codec video"
date: 2020-05-19
forum: Multimedia Software
---

### Post by gipsyshadow on 2020-05-19
I'm running ubuntu 18.04.1 with 4.18.0-25 kernel (because it's the latest one that doesn't freeze my ubuntu graphics) and I'm running VLC 3.0.8. I've got some MKV files and every time I open them with VLC I can only hear audio but video doesn't play. I tried to watch them with vlc in win10 and they play perfectly.
That's the error message I get
> 
Codec not supported
VLC could not decode the format "av01" (AOMedia's AV1 Video)

These are some MKV file details:
```

Format                                   : Matroska
Format version                           : Version 4 / Version 2
File size                                : 162 MiB
Duration                                 : 1 h 0 min
Overall bit rate                         : 377 kb/s
Writing application                      : Lavf58.12.100
Writing library                          : Lavf58.12.100
ErrorDetectionType                       : Per level 1

Video
ID                                       : 1
Format                                   : V_AV1
Codec ID                                 : V_AV1
Duration                                 : 1 h 0 min
Width                                    : 848 pixels
Height                                   : 480 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 25.000 FPS
Color space                              : YUV
Title                                    : ISO Media file produced by Google Inc.
Default                                  : Yes
Forced                                   : No
Color range                              : Limited
Color primaries                          : BT.709
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.709

```
How to solve?

---

### Post by CelticWarrior on 2020-05-19
The situation probably is the same since this Q&A: [https://askubuntu.com/questions/1061908/how-to-encode-and-playback-video-with-the-av1-codec-on-bionic-beaver-18-04](https://askubuntu.com/questions/1061908/how-to-encode-and-playback-video-with-the-av1-codec-on-bionic-beaver-18-04)

---

### Post by gipsyshadow on 2020-05-19
Well, I'm very newbie anyway I guess there's a hope with vlc:
> 
vlc: Downloaded from the Bionic Beaver Repository does not support AV1 files. This support could be compiled in from vlc version 3.0 and greater. See screenshot below...

it seems to work but how to compile and especially... what does "compile" mean? :) Could you please tell me what to do step-by-step?

Another question about that:
> 
Going to Firefox's about:config page and setting media.av1.enabled to true. Firefox 63.0 and newer have built-in AV1 support but it's currently disabled by default.

My problem deals with vlc and mkv BUT I wander if it could be possible to play a local mkv file within firefox 75.0, I mean using FF as a player.

---

### Post by CelticWarrior on 2020-05-19
If - and it's a big if - the support was added to versions 3.x you don't need to compile from source and you already have that version. Ubuntu 20.04 has by default 3.0.10. Version 4.0 (dev branch) also available as snap.

According to one of the answers (in 2018) the beta (snap) version has support already. So, you may uninstall the VLC you have now which is probably the standard software in the Ubuntu repositories for 18.04 and then install the beta snap:

```
sudo snap install vlc --beta
```
(or replace --beta with --edge if you're brave enough to install the bleeding edge 4.0.x version).


Finally, this thread title is wrong and misleading. The problem has nothing to do with MKV. MKV is just a container. The problem is the proprietary codec used withing the AV streams inside the container.

---

### Post by gipsyshadow on 2020-05-19
Ok, so let's try that "IF". Before that, I mean before removing my standard apt-vlc and installing snap-vlc, I want to ask something. I've just read something about the differences between apt installing and snap installing and these are my questions:
1) will snap installation be as easy as the apt one?
2) (if I've understood all) can I install newer vlc versions release by release via apt to test if they'll play "av01" properly and, if yes, remove snap-installed-vlc and keep the ubuntu standard-apt-vlc?

> **CelticWarrior said:**
> The problem is the proprietary codec used withing the AV streams inside the container. 
Now I see. Unfortunately I can't edit the title itself, sorry.

---

### Post by DuckHook on 2020-05-19
> **gipsyshadow said:**
> …Unfortunately I can't edit the title itself, sorry.
The owner of a thread (you) can edit the thread title, but you must go into "advanced reply" where title can be edited above the comment window. I have already done this for you for this whole thread.

---

### Post by SeijiSensei on 2020-05-19
Try this.  Install mpv and smplayer:

```
sudo apt install mpv smplayer
```

In my experience mpv plays everything I throw at it.  I don't know why it's not the primary video player (with SMPlayer as the GUI front-end) on Ubuntu.

---

### Post by monkeybrain20122 on 2020-05-19
> **SeijiSensei said:**
> Try this.  Install mpv and smplayer:

```
sudo apt install mpv smplayer
```

See if they play with that software.  It appears that mpv now has support for AV1, but that may be in newer builds.  

In my experience mpv plays everything I throw at it.  I don't know why it's not the primary video player (with SMPlayer as the GUI front-end) on Ubuntu.

The stock build is probably too old or crippled. I recommend mc3man's [ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests").

---

### Post by gipsyshadow on 2020-05-20
I've just tried with smplayer and I've got the following error:
```

/usr/bin/mpv --no-config --no-quiet --terminal --no-msg-color --input-file=/dev/stdin --no-fs --hwdec=no --sub-auto=fuzzy --no-input-default-bindings --input-vo-keyboard=no --no-input-cursor --cursor-autohide=no --no-keepaspect --wid=60817446 --monitorpixelaspect=1 --osd-level=1 --osd-scale=1 --osd-bar-align-y=0.6 --sub-ass --embeddedfonts --sub-ass-line-spacing=0 --sub-scale=1 --sub-font=Arial --sub-color=#ffffffff --sub-shadow-color=#ff000000 --sub-border-color=#ff000000 --sub-border-size=0.75 --sub-shadow-offset=2.5 --sub-font-size=50 --sub-bold=no --sub-italic=no --sub-codepage=ISO-8859-1 --sub-pos=100 --volume=55 --cache=auto --screenshot-template=cap_%F_%p_%02n --screenshot-format=jpg --screenshot-directory=/home/master/Immagini/smplayer_screenshots --audio-pitch-correction=yes --volume-max=110 --term-playing-msg=MPV_VERSION=${=mpv-version:}
INFO_VIDEO_WIDTH=${=width}
INFO_VIDEO_HEIGHT=${=height}
INFO_VIDEO_ASPECT=${=video-aspect}
INFO_VIDEO_FPS=${=container-fps:${=fps}}
INFO_VIDEO_FORMAT=${=video-format}
INFO_VIDEO_CODEC=${=video-codec}
INFO_AUDIO_FORMAT=${=audio-codec-name}
INFO_AUDIO_CODEC=${=audio-codec}
INFO_AUDIO_RATE=${=audio-params/samplerate}
INFO_AUDIO_NCH=${=audio-params/channel-count}
INFO_LENGTH=${=duration:${=length}}
INFO_DEMUXER=${=current-demuxer:${=demuxer}}
INFO_SEEKABLE=${=seekable}
INFO_TITLES=${=disc-titles}
INFO_CHAPTERS=${=chapters}
INFO_TRACKS_COUNT=${=track-list/count}
METADATA_TITLE=${metadata/by-key/title:}
METADATA_ARTIST=${metadata/by-key/artist:}
METADATA_ALBUM=${metadata/by-key/album:}
METADATA_GENRE=${metadata/by-key/genre:}
METADATA_DATE=${metadata/by-key/date:}
METADATA_TRACK=${metadata/by-key/track:}
METADATA_COPYRIGHT=${metadata/by-key/copyright:}
INFO_MEDIA_TITLE=${=media-title:}
INFO_STREAM_PATH=${stream-path}
 --audio-client-name=SMPlayer --term-status-msg=STATUS: ${=time-pos} / ${=duration:${=length:0}} P: ${=pause} B: ${=paused-for-cache} I: ${=core-idle} VB: ${=video-bitrate:0} AB: ${=audio-bitrate:0} /media/master/STORAGE/XYZ.mkv

Playing: XYZ.mkv
[mkv] Unknown/unsupported CodecID (V_AV1) or missing/bad CodecPrivate data (track 1).
 (+) Video --vid=1 (*) ( 848x480 25.000fps)
 (+) Audio --aid=1 --alang=eng (*) (opus 2ch 48000Hz)
Failed to initialize a video decoder for codec ''.
Video: no video
Exiting... (Errors when loading file)

```
in particular "Unknown/unsupported CodecID (V_AV1)".

> **monkeybrain20122 said:**
> The stock build is probably too old or crippled. I recommend mc3man's [ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests").
if I understood well, I've to paste that in my terminal
```

sudo add-apt-repository ppa:mc3man/mpv-tests
sudo apt-get update

```
have I to do something else or just that?

---

### Post by SeijiSensei on 2020-05-20
Yes, after you've installed the repository and updated you need to run
```
sudo apt install mpv
```
It will replace your current version with the one in the repository.

---

### Post by gipsyshadow on 2020-05-21
The latest mpv (version 2:0.32.0+git4~bionic1) and smplayer (version 18.2.2~ds0-1) failed too. I've just removed them via ubuntu software and then their repos.
Now I'm going to try to install vlc via snap along with my "stock" vlc, I hope not to do a mess :)

---

### Post by SeijiSensei on 2020-05-21
See if it works by forcing mpv to use its av1 codec.  It could be a problem arising from the naming scheme used by the video:

```
mpv -vd libaom-av1 /path/to/video/file
```

To see all the codecs available in mpv, use the command "mpv -vd help".

---

### Post by gipsyshadow on 2020-05-21
it works! thank you SeijiSensei :)
the codec was available for mpv
```

~$ mpv -vd help
Video decoders:
    aasc - Autodesk RLE
    aic - Apple Intermediate Codec
    alias_pix - Alias/Wavefront PIX image
    agm - Amuse Graphics Movie
    amv - AMV Video
    anm - Deluxe Paint Animation
    ansi - ASCII/ANSI art
    apng - APNG (Animated Portable Network Graphics) image
    arbc - Gryphon's Anim Compressor
    asv1 - ASUS V1
    asv2 - ASUS V2
    aura - Auravision AURA
    aura2 - Auravision Aura 2
    avrp - Avid 1:1 10-bit RGB Packer
    avrn - Avid AVI Codec
    avs - AVS (Audio Video Standard) video
    avui - Avid Meridien Uncompressed
    ayuv - Uncompressed packed MS 4:4:4:4
    bethsoftvid - Bethesda VID video
    bfi - Brute Force & Ignorance
    binkvideo - Bink video
    bitpacked - Bitpacked
    bmp - BMP (Windows and OS/2 bitmap)
    bmv_video - Discworld II BMV video
    brender_pix - BRender PIX image
    c93 - Interplay C93
    cavs - Chinese AVS (Audio Video Standard) (AVS1-P2, JiZhun profile)
    cdgraphics - CD Graphics video
    cdtoons - CDToons video
    cdxl - Commodore CDXL video
    cfhd - Cineform HD
    cinepak - Cinepak
    clearvideo - Iterated Systems ClearVideo
    cljr - Cirrus Logic AccuPak
    cllc - Canopus Lossless Codec
    cpia - CPiA video format
    camstudio (cscd) - CamStudio
    cyuv - Creative YUV (CYUV)
    dds - DirectDraw Surface image decoder
    dfa - Chronomaster DFA
    dirac - BBC Dirac VC-2
    dnxhd - VC3/DNxHD
    dpx - DPX (Digital Picture Exchange) image
    dsicinvideo - Delphine Software International CIN video
    dvvideo - DV (Digital Video)
    dxa - Feeble Files/ScummVM DXA
    dxtory - Dxtory
    dxv - Resolume DXV
    eacmv (cmv) - Electronic Arts CMV video
    eamad (mad) - Electronic Arts Madcow Video
    eatgq (tgq) - Electronic Arts TGQ video
    eatgv (tgv) - Electronic Arts TGV video
    eatqi (tqi) - Electronic Arts TQI Video
    8bps - QuickTime 8BPS video
    escape124 - Escape 124
    escape130 - Escape 130
    exr - OpenEXR image
    ffv1 - FFmpeg video codec #1
    ffvhuff - Huffyuv FFmpeg variant
    fic - Mirillis FIC
    fits - Flexible Image Transport System
    flashsv - Flash Screen Video v1
    flashsv2 - Flash Screen Video v2
    flic - Autodesk Animator Flic video
    flv (flv1) - FLV / Sorenson Spark / Sorenson H.263 (Flash Video)
    fmvc - FM Screen Capture Codec
    4xm - 4X Movie
    fraps - Fraps
    frwu - Forward Uncompressed
    g2m - Go2Meeting
    gdv - Gremlin Digital Video
    gif - GIF (Graphics Interchange Format)
    h261 - H.261
    h263 - H.263 / H.263-1996, H.263+ / H.263-1998 / H.263 version 2
    h263i - Intel H.263
    h263p - H.263 / H.263-1996, H.263+ / H.263-1998 / H.263 version 2
    h263_v4l2m2m (h263) - V4L2 mem2mem H.263 decoder wrapper
    h264 - H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
    h264_v4l2m2m (h264) - V4L2 mem2mem H.264 decoder wrapper
    hap - Vidvox Hap
    hevc - HEVC (High Efficiency Video Coding)
    hnm4video - HNM 4 video
    hq_hqa - Canopus HQ/HQA
    hqx - Canopus HQX
    huffyuv - Huffyuv / HuffYUV
    hymt - HuffYUV MT
    idcinvideo (idcin) - id Quake II CIN video
    iff (iff_ilbm) - IFF ACBM/ANIM/DEEP/ILBM/PBM/RGB8/RGBN
    imm4 - Infinity IMM4
    imm5 - Infinity IMM5
    indeo2 - Intel Indeo 2
    indeo3 - Intel Indeo 3
    indeo4 - Intel Indeo Video Interactive 4
    indeo5 - Intel Indeo Video Interactive 5
    interplayvideo - Interplay MVE video
    jpeg2000 - JPEG 2000
    jpegls - JPEG-LS
    jv - Bitmap Brothers JV video
    kgv1 - Kega Game Video
    kmvc - Karl Morton's video codec
    lagarith - Lagarith lossless
    loco - LOCO
    lscr - LEAD Screen Capture
    m101 - Matrox Uncompressed SD
    magicyuv - MagicYUV video
    mdec - Sony PlayStation MDEC (Motion DECoder)
    mimic - Mimic
    mjpeg - MJPEG (Motion JPEG)
    mjpegb - Apple MJPEG-B
    mmvideo - American Laser Games MM Video
    motionpixels - Motion Pixels video
    mpeg1video - MPEG-1 video
    mpeg2video - MPEG-2 video
    mpeg4 - MPEG-4 part 2
    mpeg4_v4l2m2m (mpeg4) - V4L2 mem2mem MPEG4 decoder wrapper
    mpegvideo (mpeg2video) - MPEG-1 video
    mpeg1_v4l2m2m (mpeg1video) - V4L2 mem2mem MPEG1 decoder wrapper
    mpeg2_v4l2m2m (mpeg2video) - V4L2 mem2mem MPEG2 decoder wrapper
    msa1 - MS ATC Screen
    mscc - Mandsoft Screen Capture Codec
    msmpeg4v1 - MPEG-4 part 2 Microsoft variant version 1
    msmpeg4v2 - MPEG-4 part 2 Microsoft variant version 2
    msmpeg4 (msmpeg4v3) - MPEG-4 part 2 Microsoft variant version 3
    msrle - Microsoft RLE
    mss1 - MS Screen 1
    mss2 - MS Windows Media Video V9 Screen
    msvideo1 - Microsoft Video 1
    mszh - LCL (LossLess Codec Library) MSZH
    mts2 - MS Expression Encoder Screen
    mvc1 - Silicon Graphics Motion Video Compressor 1
    mvc2 - Silicon Graphics Motion Video Compressor 2
    mvdv - MidiVid VQ
    mvha - MidiVid Archive Codec
    mwsc - MatchWare Screen Capture Codec
    mxpeg - Mobotix MxPEG video
    nuv - NuppelVideo/RTJPEG
    paf_video - Amazing Studio Packed Animation File Video
    pam - PAM (Portable AnyMap) image
    pbm - PBM (Portable BitMap) image
    pcx - PC Paintbrush PCX image
    pgm - PGM (Portable GrayMap) image
    pgmyuv - PGMYUV (Portable GrayMap YUV) image
    pictor - Pictor/PC Paint
    pixlet - Apple Pixlet
    png - PNG (Portable Network Graphics) image
    ppm - PPM (Portable PixelMap) image
    prores - ProRes (iCodec Pro)
    prosumer - Brooktree ProSumer Video
    psd - Photoshop PSD file
    ptx - V.Flash PTX image
    qdraw - Apple QuickDraw
    qpeg - Q-team QPEG
    qtrle - QuickTime Animation (RLE) video
    r10k - AJA Kona 10-bit RGB Codec
    r210 - Uncompressed RGB 10-bit
    rasc - RemotelyAnywhere Screen Capture
    rawvideo - raw video
    rl2 - RL2 video
    roqvideo (roq) - id RoQ video
    rpza - QuickTime video (RPZA)
    rscc - innoHeim/Rsupport Screen Capture Codec
    rv10 - RealVideo 1.0
    rv20 - RealVideo 2.0
    rv30 - RealVideo 3.0
    rv40 - RealVideo 4.0
    sanm - LucasArts SANM/Smush video
    scpr - ScreenPressor
    screenpresso - Screenpresso
    sgi - SGI image
    sgirle - Silicon Graphics RLE 8-bit video
    sheervideo - BitJazz SheerVideo
    smackvid (smackvideo) - Smacker video
    smc - QuickTime Graphics (SMC)
    smvjpeg - SMV JPEG
    snow - Snow
    sp5x - Sunplus JPEG (SP5X)
    speedhq - NewTek SpeedHQ
    srgc - Screen Recorder Gold Codec
    sunrast - Sun Rasterfile image
    svq1 - Sorenson Vector Quantizer 1 / Sorenson Video 1 / SVQ1
    svq3 - Sorenson Vector Quantizer 3 / Sorenson Video 3 / SVQ3
    targa - Truevision Targa image
    targa_y216 - Pinnacle TARGA CineWave YUV16
    tdsc - TDSC
    theora - Theora
    thp - Nintendo Gamecube THP video
    tiertexseqvideo - Tiertex Limited SEQ video
    tiff - TIFF image
    tmv - 8088flex TMV
    truemotion1 - Duck TrueMotion 1.0
    truemotion2 - Duck TrueMotion 2.0
    truemotion2rt - Duck TrueMotion 2.0 Real Time
    camtasia (tscc) - TechSmith Screen Capture Codec
    tscc2 - TechSmith Screen Codec 2
    txd - Renderware TXD (TeXture Dictionary) image
    ultimotion (ulti) - IBM UltiMotion
    utvideo - Ut Video
    v210 - Uncompressed 4:2:2 10-bit
    v210x - Uncompressed 4:2:2 10-bit
    v308 - Uncompressed packed 4:4:4
    v408 - Uncompressed packed QT 4:4:4:4
    v410 - Uncompressed 4:4:4 10-bit
    vb - Beam Software VB
    vble - VBLE Lossless Codec
    vc1 - SMPTE VC-1
    vc1image - Windows Media Video 9 Image v2
    vc1_v4l2m2m (vc1) - V4L2 mem2mem VC1 decoder wrapper
    vcr1 - ATI VCR1
    vmdvideo - Sierra VMD video
    vmnc - VMware Screen Codec / VMware Video
    vp3 - On2 VP3
    vp4 - On2 VP4
    vp5 - On2 VP5
    vp6 - On2 VP6
    vp6a - On2 VP6 (Flash version, with alpha channel)
    vp6f - On2 VP6 (Flash version)
    vp7 - On2 VP7
    vp8 - On2 VP8
    vp8_v4l2m2m (vp8) - V4L2 mem2mem VP8 decoder wrapper
    vp9 - Google VP9
    vp9_v4l2m2m (vp9) - V4L2 mem2mem VP9 decoder wrapper
    vqavideo (ws_vqa) - Westwood Studios VQA (Vector Quantized Animation) video
    webp - WebP image
    wcmv - WinCAM Motion Video
    wrapped_avframe - AVPacket to AVFrame passthrough
    wmv1 - Windows Media Video 7
    wmv2 - Windows Media Video 8
    wmv3 - Windows Media Video 9
    wmv3image - Windows Media Video 9 Image
    wnv1 - Winnov WNV1
    xan_wc3 - Wing Commander III / Xan
    xan_wc4 - Wing Commander IV / Xxan
    xbm - XBM (X BitMap) image
    xface - X-face image
    xl (vixl) - Miro VideoXL
    xpm - XPM (X PixMap) image
    xwd - XWD (X Window Dump) image
    y41p - Uncompressed YUV 4:1:1 12-bit
    ylc - YUY2 Lossless Codec
    yop - Psygnosis YOP Video
    yuv4 - Uncompressed packed 4:2:0
    012v - Uncompressed 4:2:2 10-bit
    zerocodec - ZeroCodec Lossless Video
    zlib - LCL (LossLess Codec Library) ZLIB
    zmbv - Zip Motion Blocks Video
    libdav1d (av1) - dav1d AV1 decoder by VideoLAN
    libvpx (vp8) - libvpx VP8
    libvpx-vp9 (vp9) - libvpx VP9
    bintext - Binary text
    xbin - eXtended BINary text
    idf - iCEDraw text
    h264_cuvid (h264) - Nvidia CUVID H264 decoder
    hevc_cuvid (hevc) - Nvidia CUVID HEVC decoder
    mjpeg_cuvid (mjpeg) - Nvidia CUVID MJPEG decoder
    mpeg1_cuvid (mpeg1video) - Nvidia CUVID MPEG1VIDEO decoder
    mpeg2_cuvid (mpeg2video) - Nvidia CUVID MPEG2VIDEO decoder
    mpeg4_cuvid (mpeg4) - Nvidia CUVID MPEG4 decoder
    vc1_cuvid (vc1) - Nvidia CUVID VC1 decoder
    vp8_cuvid (vp8) - Nvidia CUVID VP8 decoder
    vp9_cuvid (vp9) - Nvidia CUVID VP9 decoder

```
in particular "libdav1d (av1) - dav1d AV1 decoder by VideoLAN"
and that's what i get running your command
```

~$ mpv -vd libaom-av1 /media/...../XYZ.mkv
 (+) Video --vid=1 (*) (av1 848x480 25.000fps)
 (+) Audio --aid=1 --alang=eng (*) (opus 2ch 48000Hz)
AO: [pulse] 48000Hz stereo 2ch float
VO: [gpu] 848x480 yuv420p
AV: 00:00:04 / 01:00:00 (0%) A-V:  0.000 Cache: 1771s/150MB

```
i've just tried also with
```

smplayer -vd libaom-av1 /media/...../XYZ.mkv

```
but i've got this error message
```

/usr/bin/mpv --no-config --no-quiet --terminal --no-msg-color --input-file=/dev/stdin --no-fs --hwdec=no --sub-auto=fuzzy --no-input-default-bindings --input-vo-keyboard=no --no-input-cursor --cursor-autohide=no --no-keepaspect --wid=58720275 --monitorpixelaspect=1 --osd-level=1 --osd-scale=1 --osd-bar-align-y=0.6 --sub-ass --embeddedfonts --sub-ass-line-spacing=0 --sub-scale=1 --sub-font=Arial --sub-color=#ffffffff --sub-shadow-color=#ff000000 --sub-border-color=#ff000000 --sub-border-size=0.75 --sub-shadow-offset=2.5 --sub-font-size=50 --sub-bold=no --sub-italic=no --sub-codepage=ISO-8859-1 --sub-pos=100 --volume=55 --cache=auto --screenshot-template=cap_%F_%p_%02n --screenshot-format=jpg --screenshot-directory=/home/master/Immagini/smplayer_screenshots --audio-pitch-correction=yes --volume-max=110 --ytdl --term-playing-msg=MPV_VERSION=${=mpv-version:}
INFO_VIDEO_WIDTH=${=width}
INFO_VIDEO_HEIGHT=${=height}
INFO_VIDEO_ASPECT=${=video-aspect}
INFO_VIDEO_FPS=${=container-fps:${=fps}}
INFO_VIDEO_FORMAT=${=video-format}
INFO_VIDEO_CODEC=${=video-codec}
INFO_AUDIO_FORMAT=${=audio-codec-name}
INFO_AUDIO_CODEC=${=audio-codec}
INFO_AUDIO_RATE=${=audio-params/samplerate}
INFO_AUDIO_NCH=${=audio-params/channel-count}
INFO_LENGTH=${=duration:${=length}}
INFO_DEMUXER=${=current-demuxer:${=demuxer}}
INFO_SEEKABLE=${=seekable}
INFO_TITLES=${=disc-titles}
INFO_CHAPTERS=${=chapters}
INFO_TRACKS_COUNT=${=track-list/count}
METADATA_TITLE=${metadata/by-key/title:}
METADATA_ARTIST=${metadata/by-key/artist:}
METADATA_ALBUM=${metadata/by-key/album:}
METADATA_GENRE=${metadata/by-key/genre:}
METADATA_DATE=${metadata/by-key/date:}
METADATA_TRACK=${metadata/by-key/track:}
METADATA_COPYRIGHT=${metadata/by-key/copyright:}
INFO_MEDIA_TITLE=${=media-title:}
INFO_STREAM_PATH=${stream-path}
 --audio-client-name=SMPlayer --term-status-msg=STATUS: ${=time-pos} / ${=duration:${=length:0}} P: ${=pause} B: ${=paused-for-cache} I: ${=core-idle} VB: ${=video-bitrate:0} AB: ${=audio-bitrate:0} -vd

Error parsing option input-file (option not found)
Setting commandline option --input-file=/dev/stdin failed.
Exiting... (Fatal error)

```

last but not the least important thing: is it possible to do the same job for my current vlc or it works only for mpv?

---

### Post by mc4man on 2020-05-21
> **gipsyshadow said:**
> it works! thank you SeijiSensei :)
the codec was available for mpv

in particular "libdav1d (av1) - dav1d AV1 decoder by VideoLAN"
and that's what i get running your command
```

~$ mpv -vd libaom-av1 /media/...../XYZ.mkv
 (+) Video --vid=1 (*) (av1 848x480 25.000fps)
 (+) Audio --aid=1 --alang=eng (*) (opus 2ch 48000Hz)
AO: [pulse] 48000Hz stereo 2ch float
VO: [gpu] 848x480 yuv420p
AV: 00:00:04 / 01:00:00 (0%) A-V:  0.000 Cache: 1771s/150MB

```

last but not the least important thing: is it possible to do the same job for my current vlc or it works only for mpv?

To clear up - 
My current 18.04 mpv build does not have libaom enabled in ffmpeg, the 20.04 build does. I added it for rare cases where libaom performs better than libdav1d, usually for 10bit encodes. Likely the next 18.04 build will get libaom as an option , note that current ffmpeg defaults to libdav1d.

So, your using -vd libaom-av1 has no effect and is ignored by mpv. While playing a vid go shift+i  to get an overlay that would include decoder used.
Using just plain mpv /media/...../XYZ.mkv should work fine.

As far as smplayer or even gnome-mpv they also should work with no issue, no particular config needed, see screen.
In your case the smplayer you have is too old for recent mpv, error is "Error parsing option input-file (option not found)"
This was fixed in latest smplayer release, use the smplayer ppa.

edit: additionally, the snap version of vlc supports av1 thru libdav1d, .deb versions need libavcodecXX to have av1 support..

---

### Post by SeijiSensei on 2020-05-22
To pass parameters like "-vd codec" to mpv in SMPlayer I believe you need to add them via Options > Advanced > Mplayer/mpv. I've never tried using them on the command line.

---

### Post by gipsyshadow on 2020-05-22
> **mc4man said:**
> So, your using -vd libaom-av1 has no effect and is ignored by mpv. [...] Using just plain mpv /media/...../XYZ.mkv should work fine.
ok, sorry but i was a bit confused about that. what i can tell is: before the SeijiSensei command mpv didn't play my mkv and after it played. now it plays that mkv without command line ("plain mpv"), i just don't know why.

> **mc4man said:**
> 
In your case the smplayer you have is too old for recent mpv [...] use the smplayer ppa
ok, i solved "again" and now my mkv plays with smplayer 20.4.2. i ran the following commands:
```

sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update
sudo apt-get install smplayer smtube smplayer-themes smplayer-skins

```
and i've just removed mpv player via sw center and then its repos because one av1 codec player is enough.
by the way: could i remove "smtube smplayer-themes smplayer-skins" now? i just need the "stock" player.

> **mc4man said:**
> 
edit: additionally, the snap version of vlc supports av1 thru libdav1d, .deb versions need libavcodecXX to have av1 support.. 

i don't know if it can be "interesting" to get the latest vlc installed via snap, what do you suggest me? i see only the av1 codec playing advantage but what about drawbacks?

note @SeijiSensei, just for my future knowledge
i've tried to paste "-vd libdav1d" and then "-vd libaom-av1" too within "options" and then within "video filters" in smplayer but that error remained. did you mean to do that?

---

### Post by mc4man on 2020-05-22
> **gipsyshadow said:**
> ok, sorry but i was a bit confused about that. what i can tell is: before the SeijiSensei command mpv didn't play my mkv and after it played. now it plays that mkv without command line ("plain mpv"), i just don't know why.


ok, i solved "again" and now my mkv plays with smplayer 20.4.2. i ran the following commands:
```

sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update
sudo apt-get install smplayer smtube smplayer-themes smplayer-skins

```
and i've just removed mpv player via sw center and then its repos because one av1 codec player is enough.
by the way: could i remove "smtube smplayer-themes smplayer-skins" now? i just need the "stock" player.



i don't know if it can be "interesting" to get the latest vlc installed via snap, what do you suggest me? i see only the av1 codec playing advantage but what about drawbacks?

note @SeijiSensei, just for my future knowledge
i've tried to paste "-vd libdav1d" and then "-vd libaom-av1" too within "options" and then within "video filters" in smplayer but that error remained. did you mean to do that?

I find this post^ a bit confusing..

smplayer can't play anything by itself, it's just a frontend. It uses either mpv or mplayer. So if you remove ppa mpv it'll use mplayer or repo mpv. In either case there is no support for av1.

Adding -vd libdav1d to options in smplayer is unnecessary, it's the default. Adding -vd libaom-av1 to smplayer in 18.04 is a waste as currently not supported.

The"latest"vlc snap, i.e 4.x is quite a change for vlc, I would never use.  The 3.9.2 vlc snap is ok but tedious to browse to files..

screen shows option added to smplayer in 20.04 where it would have the intended effect  (though libaom is a poor choice most of the time..

---

### Post by gipsyshadow on 2020-05-23
sorry, it was my fault because i'm very newbie. now i see smplayer's just a frontend and i see my misunderstanding.

now i'd like to understand what a snap installation of 3.9.2 vlc could mean for my personal case, i mean for my graphics issues because sometimes my ubuntu freezes due to that. in other words i've to evaluate if it's better to have stock vlc + smplayer (just to play av1 codec videos) or get only snap 3.9.2 vlc for everything.
so how to install 3.9.2 vlc via snap?

---

### Post by mc4man on 2020-05-23
> **gipsyshadow said:**
> sorry, it was my fault because i'm very newbie. now i see smplayer's just a frontend and i see my misunderstanding.

now i'd like to understand what a snap installation of 3.9.2 vlc could mean for my personal case, i mean for my graphics issues because sometimes my ubuntu freezes due to that. in other words i've to evaluate if it's better to have stock vlc + smplayer (just to play av1 codec videos) or get only snap 3.9.2 vlc for everything.
so how to install 3.9.2 vlc via snap?You would have to try it and decide for yourself.
To make easier remove the .deb vlc if installed, this will remove all vlc packages, typically 15..
```

sudo apt-get purge vlc*.
```
Then install the snap version
```
sudo snap install vlc
```
When done open vlc as you've previously done.

To go back,
```
sudo snap remove vlc
```
```
sudo apt install vlc
```

---

