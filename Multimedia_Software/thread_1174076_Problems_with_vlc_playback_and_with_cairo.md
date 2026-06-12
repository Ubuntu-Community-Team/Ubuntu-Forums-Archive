---
title: "Problems with vlc playback and with cairo"
date: 2009-05-30
forum: Multimedia Software
---

### Post by aloasi on 2009-05-30
Hello, I run Ubuntu 9.04 i downloaded VLC player the version 1.0.0 rc Goldeneye and it worked fine everything played. After a few days it started crashing whenever i would play a .avi file, i googled the problem i had and came up with this site [http://www.compmaui.com/video-playback-crashes-in-ubuntu-904-a-simple-fix-293.html](http://www.compmaui.com/video-playback-crashes-in-ubuntu-904-a-simple-fix-293.html) and it said that he had the same problem to fix it he ran this command 
 ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I dit it and it fixed the video playback but now cairo-dock when it starts i run it with open gl, when you put you mouse over it, it kind of looks like there is another dock behind it and it continues to do that everytime you put the cursor on top of it. I tried to run it with out open gl and the back of the dock was black it would never like blend with the background. Thankyou. Also my compiz seems to have been disabled. Is there a way to come back to what i had? i will attach  some pictures for you to see. in these pictures you could see that some icone appear to be doubled, hopefully i can get out of this rut guys thank you.

---

### Post by aloasi on 2009-05-30
I have already resolved it. I overlooked the most stupid thing, the video driver i don't know why it deactivated i activated it and voila everything is normal again.

---

### Post by aloasi on 2009-05-30
Everything works except VLC i can not play avis yet. Help

---

### Post by aloasi on 2009-05-30
help

---

### Post by aloasi on 2009-05-31
when i write vlc in command line this is what i get
```
hector@hector-desktop:~$ vlc
VLC media player 1.0.0-rc2 Goldeneye
[0x1213db8] main interface error: no interface module matched "globalhotkeys,none"
[0x1213db8] main interface error: no suitable interface module
[0xfda888] main libvlc error: interface "globalhotkeys,none" initialization failed
/home/hector/.themes/still-unamed/gtk-2.0/panel.rc:96: Unable to locate image file in pixmap_path: "Panel/panelnutton4.png"
/home/hector/.themes/still-unamed/gtk-2.0/panel.rc:99: Background image options specified without filename
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1532: Unable to locate image file in pixmap_path: "Tabs/notebookright.png"
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1542: Background image options specified without filename
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1892: Invalid symbolic color 'selected_bg_color'
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1892: error: invalid identifier `selected_bg_color', expected valid identifier
Interface initialization failed

```

---

### Post by aloasi on 2009-06-01
up

---

### Post by mc4man on 2009-06-01
Try vlc from the terminal with 
```
vlc --reset-config --reset-plugins-cache
```

---

### Post by aloasi on 2009-06-01
hi, i tried what you wrote but it didn't make it play it crashed again i got the same. Thank you. ```
hector@hector-desktop:~$ vlc --reset-config --reset-plugins-cache
VLC media player 1.0.0-rc2 Goldeneye
[0x1a51fb8] main interface error: no interface module matched "globalhotkeys,none"
[0x1a51fb8] main interface error: no suitable interface module
[0x1805888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1805888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
/home/hector/.themes/still-unamed/gtk-2.0/panel.rc:96: Unable to locate image file in pixmap_path: "Panel/panelnutton4.png"
/home/hector/.themes/still-unamed/gtk-2.0/panel.rc:99: Background image options specified without filename
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1532: Unable to locate image file in pixmap_path: "Tabs/notebookright.png"
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1542: Background image options specified without filename
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1892: Invalid symbolic color 'selected_bg_color'
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1892: error: invalid identifier `selected_bg_color', expected valid identifier
Interface initialization failed

```

---

### Post by mc4man on 2009-06-01
open this way to show the configure options
```
vlc -vv
```

The whole thing with the cairo dock plus the errors you're showing seems suspicious, maybe you should try a complete removal of vlc.

Did you build vlc or get from a ppa (kow?)

i gotta go , to do a complete removal from ppa install, search vlc in synaptic, mark everything with vlc in the name for complete removal and apply.
Then go to home folder and in .cache delete the vlc folder
In .config also delete the vlc folder

You may wish to run this to compare modules
```
doug@doug-desktop:~$ vlc -vv --list
VLC media player 1.1.0-git Goldeneye
[0x9381154] main libvlc debug: VLC media player - version 1.1.0-git Goldeneye - (c) 1996-2009 the VideoLAN team
[0x9381154] main libvlc debug: libvlc was configured with ./configure  
'--with-live555-tree=/usr/lib/live' 
'--prefix=/usr' '--disable-zvbi' '--enable-flac' 
'--enable-libass' '--enable-faad' '--disable-kate'  
 '--enable-twolame' '--enable-caca' '--enable-theora' 
'--enable-mozilla' '--with-mozilla-pkg=libxul-plugin'
 '--enable-loader'   '--with-tuning=pentium4' '--enable-static'
[0x9381154] main libvlc debug: translation test: code is "C"
[0x9381154] main libvlc debug: checking plugin modules
[0x9381154] main libvlc debug: loading plugins cache file /home/doug/.cache/vlc/plugins-04041e.dat
[0x9381154] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x9381154] main libvlc debug: module bank initialized (377 modules)
  stream_out_gather     Gathering stream output
  stream_out_transrate  MPEG2 video transrating stream output
  stream_out_raop       Remote Audio Output Protocol stream output
  stream_out_rtp        RTP stream output
  stream_out_display    Display stream output
  stream_out_standard   Standard stream output
  stream_out_duplicate  Duplicate stream output
  stream_out_autodel    Automatically add/delete input streams
  stream_out_record     Record stream output
  stream_out_transcode  Transcode stream output
  stream_out_mosaic_bridge Mosaic bridge stream output
  stream_out_bridge     Bridge stream output
  stream_out_bridge     Bridge stream output
  stream_out_bridge     Bridge stream output
  stream_out_description Description stream output
  stream_out_es         Elementary stream output
  stream_out_dummy      Dummy stream output
  stream_filter_rar     Uncompressed RAR
  stream_filter_record  Internal stream record
  decomp                Decompression
  decomp                Decompression
  xcb_window            (Experimental) XCB video window
  x11                   X11 video output
  drawable              Embedded X window video
  drawable              Embedded Windows video
  vmem                  Video memory output
  caca                  Color ASCII art video output
  xcb                   (Experimental) XCB video output
  xvideo                XVideo extension video output
  vout_sdl              Simple DirectMedia Layer video output
  opengl                OpenGL video output
  fb                    GNU/Linux framebuffer video output
  yuv                   YUV video output
  glx                   OpenGL(GLX) provider
  xcb_xv                (Experimental) XVideo output
  mtp                   MTP devices
  sap                   SAP Announcements
  sap                   SDP Descriptions parser
  bonjour               Bonjour services
  podcast               Podcasts
  hal                   HAL devices detection
  shout                 Shoutcast radio listings
  shout                 Freebox TV listing (French ISP free.fr services)
  shout                 French TV
  shout                 Shoutcast TV listings
  rc                    Remote control interface
  gestures              Mouse gestures control interface
  motion                motion control interface
  signals               POSIX signals handling interface
  dbus                  D-Bus control interface
  telnet                VLM remote control interface
  http                  HTTP remote control interface
 [COLOR="Blue"] hotkeys               Hotkeys management interface
  globalhotkeys         Global Hotkeys interface[/COLOR]
  showintf              Show interface with mouse
  visual                Visualizer filter
  mux_ogg               Ogg/OGM muxer
  mux_mp4               MP4/MOV muxer
  mux_mpjpeg            Multipart JPEG muxer
  mux_avi               AVI muxer
  mux_dummy             Dummy/Raw muxer
  mux_ps                PS muxer
  mux_wav               WAV muxer
  mux_asf               ASF muxer
[COLOR="Blue"]  qt4                   Qt interface
  qt4                   Qt interface
  qt4                   Dialogs provider[/COLOR]
  skins2                Skinnable Interface
  skins2                Skins loader demux
  skins2                Skinnable Interface
  packetizer_vc1        VC-1 packetizer
  packetizer_mpeg4video MPEG4 video packetizer
  packetizer_mpeg4audio MPEG4 audio packetizer
  packetizer_mlp        MLP/TrueHD parser
  packetizer_h264       H.264 video packetizer
  packetizer_dirac      Dirac packetizer
  packetizer_copy       Copy packetizer
  packetizer_mpegvideo  MPEG-I/II video packetizer
  motiondetect          Motion detect video filter
  canvas                Automatically resize and padd a video
  noise                 Noise video filter
  mosaic                Mosaic video sub filter
  crop                  Crop video filter
  bluescreen            Bluescreen video filter
  rotate                Rotate video filter
  blendbench            Blending benchmark filter
  osdmenu               On Screen Display menu
  extract               Extract RGB component video filter
  rss                   RSS and Atom feed display
  panoramix             Panoramix: wall with overlap video filter
  sharpen               Augment contrast between contours.
  scale                 Video scaling filter
  puzzle                Puzzle interactive game video filter
  colorthres            Color threshold filter
  deinterlace           Deinterlacing video filter
  deinterlace           Deinterlacing video filter
  invert                Invert video filter
  logo                  Logo sub filter
  logo                  Logo video filter
  clone                 Clone video filter
  yuvp                  YUVP converter
  atmo                  AtmoLight Filter
  alphamask             Alpha mask video filter
  gradient              Gradient video filter
  psychedelic           Psychedelic video filter
  postproc              Video post processing filter
  adjust                Image properties filter
  magnify               Magnify/Zoom interactive video filter
  marq                  Marquee display
  wall                  Wall video filter
  motionblur            Motion blur filter
  ripple                Ripple video filter
  erase                 Erase video filter
  gaussianblur          Gaussian blur video filter
  dynamicoverlay        Dynamic video overlay
  rv32                  RV32 conversion filter
  transform             Video transformation filter
  blend                 Video pictures blending
  croppadd              Video scaling filter
  scene                 Scene video filter
  remoteosd             Remote-OSD over VNC
  wave                  Wave video filter
  grain                 Grain video filter
  chain                 Video filtering using a chain of video filter modules
  swscale               Video scaling filter
  dummy                 Dummy interface function
  dummy                 Dummy font renderer function
  dummy                 Dummy video output function
  dummy                 Dummy audio output function
  dummy                 Dummy encoder function
  dummy                 Dump decoder function
  dummy                 Dummy decoder function
  dummy                 Dummy demux function
  dummy                 Dummy access function
  export                export
  export                HTML playlist export
  export                XSPF playlist export
  export                Old playlist export
  export                M3U playlist export
  stats                 Stats encoder function
  stats                 Stats video output function
  stats                 Stats demux function
  stats                 Stats decoder function
  memcpy                libc memcpy
  logger                File logging
  inhibit               Power Management Inhibitor
  osd_parser            osd_parser
  osd_parser            XML OSD configuration importer
  osd_parser            OSD configuration importer
  vod_rtsp              RTSP VoD server
  memcpymmx             MMX memcpy
  gnutls                GnuTLS transport layer security
  gnutls                GnuTLS server
  memcpymmxext          MMX EXT memcpy
  xml                   XML Parser (using libxml2)
  telepathy             Telepathy "Now Playing" (MissionControl)
  notify                LibNotify Notification Plugin
  audioscrobbler        Submission of played songs to last.fm
  memcpy3dn             3D Now! memcpy
  lua                   Fetch artwork using lua scripts
  lua                   Lua Interface Module
  lua                   Lua Playlist Parser Interface
  probe_hal             HAL devices detection
  xtag                  Simple XML Parser
  screensaver           X Screensaver disabler
  freetype              Freetype2 font renderer
  access_output_udp     UDP stream output
  access_output_file    File stream output
  access_output_rtmp    RTMP stream output
  access_output_http    HTTP stream output
  access_output_dummy   Dummy stream output
  oss                   UNIX OSS audio output
  alsa                  ALSA audio output
  aout_file             File audio output
  aout_sdl              Simple DirectMedia Layer audio output
  i420_ymga             Conversions from I420,IYUV,YV12 to YMGA
  i420_rgb_mmx          MMX I420,IYUV,YV12 to RV15,RV16,RV24,RV32 conversions
  i422_yuy2_mmx         MMX conversions from I422 to YUY2,YUNV,YVYU,UYVY,UYNV,Y422,IUYV,cyuv
  yuy2_i422             Conversions from YUY2,YUNV,YVYU,UYVY,UYNV,Y422,cyuv to I422
  i420_ymga_mmx         MMX conversions from I420,IYUV,YV12 to YMGA
  i420_yuy2             Conversions from I420,IYUV,YV12 to YUY2,YUNV,YVYU,UYVY,UYNV,Y422,IUYV,cyuv,Y211
  i420_yuy2_mmx         MMX conversions from I420,IYUV,YV12 to YUY2,YUNV,YVYU,UYVY,UYNV,Y422,IUYV,cyuv
  grey_yuv              Conversions from GREY to I420,YUY2
  i422_yuy2_sse2        SSE2 conversions from I422 to YUY2,YUNV,YVYU,UYVY,UYNV,Y422,IUYV,cyuv
  i420_rgb              I420,IYUV,YV12 to RGB2,RV15,RV16,RV24,RV32 conversions
  i420_rgb_sse2         SSE2 I420,IYUV,YV12 to RV15,RV16,RV24,RV32 conversions
  yuy2_i420             Conversions from YUY2,YUNV,YVYU,UYVY,UYNV,Y422,cyuv to I420
  i420_yuy2_sse2        SSE2 conversions from I420,IYUV,YV12 to YUY2,YUNV,YVYU,UYVY,UYNV,Y422,IUYV,cyuv
  i422_i420             Conversions from I422,J422 to I420,IYUV,J420,YV12,YUVA
  i422_yuy2             Conversions from I422 to YUY2,YUNV,YVYU,UYVY,UYNV,Y422,IUYV,cyuv,Y211
  access_tcp            TCP input
  access_smb            SMB input
  access_file           File input
  access_oss            OSS input
  access_mms            Microsoft Media Server (MMS) input
  dvdread               DVDRead Input (no menu support)
  dvdnav                DVDnav Input
  access_ftp            FTP input
  access_ftp            FTP upload output
  access_directory      Standard filesystem directory input
  zip                   Zip files filter
  zip                   Zip access
  access_udp            UDP input
  access_alsa           Alsa audio capture input
  rtp                   Real-Time Protocol (RTP) input
  x11_screen            Screen Input
  vcd                   VCD input
  access_mmap           Memory-mapped file input
  access_http           HTTP input
  v4l2                  Video4Linux2 input
  v4l2                  Video4Linux2 Compressed A/V
  access_fake           Fake input
  access_bd             Blu-Ray Disc Input
  access_mtp            MTP input
  access_rtmp           RTMP input
  cdda                  Audio CD input
  taglib                taglib
  taglib                taglib
  folder                Folder meta data
  spdif_mixer           Dummy S/PDIF audio mixer
  trivial_mixer         Trivial audio mixer
  float32_mixer         Float32 audio mixer
  trivial_resampler     Audio filter for trivial resampling
  headphone_channel_mixer Headphone virtual spatialization effect
  headphone_channel_mixer Headphone virtual spatialization effect
  converter_fixed       Fixed point audio format conversions
  converter_fixed       Fixed point audio format conversions
  converter_fixed       Fixed point audio format conversions
  converter_fixed       Fixed point audio format conversions
  a52tospdif            Audio filter for A/52->S/PDIF encapsulation
  equalizer             Equalizer with 10 bands
  normvol               Volume normalizer
  audio_format          Audio filter for PCM format conversion
  simple_channel_mixer  Audio filter for simple channel mixing
  simple_channel_mixer  audio filter for simple channel mixing
  ugly_resampler        Audio filter for ugly resampling
  linear_resampler      Audio filter for linear interpolation resampling
  linear_resampler      Audio filter for linear interpolation resampling
  mono                  Audio filter for stereo to mono conversion
  mpgatofixed32         MPEG audio decoder
  mpgatofixed32         MPEG audio decoder
  param_eq              Parametric Equalizer
  bandlimited_resampler Audio filter for band-limited interpolation resampling
  bandlimited_resampler Audio filter for band-limited interpolation resampling
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  converter_float       Floating-point audio format conversions
  trivial_channel_mixer Audio filter for trivial channel mixing
  spatializer           Audio Spatializer
  a52tofloat32          ATSC A/52 (AC-3) audio decoder
  a52tofloat32          ATSC A/52 (AC-3) audio decoder
  scaletempo            Audio tempo scaler synched with rate
  dolby_surround_decoder Simple decoder for Dolby Surround encoded streams
  dtstospdif            Audio filter for DTS->S/PDIF encapsulation
  dtstofloat32          DTS Coherent Acoustics audio decoder
  dtstofloat32          DTS Coherent Acoustics audio decoder
  au                    AU demuxer
  flacsys               FLAC demuxer
  rawvid                Raw video demuxer
  playlist              Playlist
  playlist              ZPL playlist import
  playlist              WPL playlist import
  playlist              iTunes Music Library importer
  playlist              Dummy ifo demux
  playlist              Google Video Playlist importer
  playlist              QuickTime Media Link importer
  playlist              Kasenna MediaBase parser
  playlist              ASX playlist import
  playlist              New winamp 5.2 shoutcast import
  playlist              XSPF playlist import
  playlist              Podcast parser
  playlist              DVB playlist import
  playlist              B4S playlist import
  playlist              PLS playlist import
  playlist              RAM playlist import
  playlist              M3U playlist import
  live555               RTP/RTSP/SDP demuxer (using Live555)
  live555               RTSP/RTP access and demux
  mjpeg                 M-JPEG camera demuxer
  vobsub                Vobsub subtitles parser
  es                    MPEG-I/II/4 / A52 / DTS / MLP audio
  dirac                 Dirac video demuxer
  real                  Real demuxer
  asf                   ASF v1.0 demuxer
  ty                    TY Stream audio/video demux
  mpgv                  MPEG-I/II video demuxer
  demux_cdg             CDG demuxer
  aiff                  AIFF demuxer
  rawdv                 DV (Digital Video) demuxer
  h264                  H264 video demuxer
  vc1                   VC1 video demuxer
  nuv                   Nuv demuxer
  avformat              FFmpeg demuxer
  avformat              FFmpeg muxer
  pva                   PVA demuxer
  smf                   SMF demuxer
  xa                    XA demuxer
  ogg                   OGG demuxer
  tta                   TTA demuxer
  m4v                   MPEG-4 video demuxer
  avi                   AVI demuxer
  wav                   WAV demuxer
  nsv                   NullSoft demuxer
  subtitle              Text subtitles parser
  voc                   VOC demuxer
  nsc                   Windows Media NSC metademux
  rawaud                Raw audio demuxer
  demuxdump             File dumper
  ps                    MPEG-PS demuxer
  ps                    MPEG-PS demuxer
  mkv                   Matroska stream demuxer
  mp4                   MP4 stream demuxer
  subsusf               USF subtitles decoder
  faad                  AAC audio decoder (using libfaad2)
  speex                 Speex audio decoder
  speex                 Speex audio encoder
  speex                 Speex audio packetizer
  cmml                  CMML annotations decoder
  cmml                  CMML annotations decoder
  libass                Subtitle renderers using libass
  subsdec               Text subtitles decoder
  adpcm                 ADPCM audio decoder
  araw                  Raw/Log Audio decoder
  araw                  Raw audio encoder
  spudec                DVD subtitles decoder
  spudec                DVD subtitles packetizer
  x264                  H.264/MPEG4 AVC encoder (x264)
  cc                    Closed Captions decoder
  fake                  Fake video decoder
  libmpeg2              MPEG I/II video decoder (using libmpeg2)
  png                   PNG video decoder
  t140                  T.140 text encoder
  invmem                Memory video decoder
  dmo                   DirectMedia Object decoder
  dmo                   DirectMedia Object encoder
  theora                Theora video decoder
  theora                Theora video encoder
  theora                Theora video packetizer
  cdg                   CDG video decoder
  flac                  Flac audio decoder
  flac                  Flac audio packetizer
  flac                  Flac audio encoder
  telx                  Teletext subtitles decoder
  mpeg_audio            MPEG audio layer I/II/III decoder
  mpeg_audio            MPEG audio layer I/II/III packetizer
  cvdsub                CVD subtitle decoder
  cvdsub                Chaoji VCD subtitle packetizer
  svcdsub               Philips OGT (SVCD subtitle) decoder
  svcdsub               Philips OGT (SVCD subtitle) packetizer
  rawvideo              Pseudo raw video decoder
  rawvideo              Pseudo raw video packetizer
  dts                   DTS parser
  dts                   DTS audio packetizer
  a52                   A/52 parser
  a52                   A/52 audio packetizer
  dvbsub                DVB subtitles decoder
  dvbsub                DVB subtitles encoder
  aes3                  AES3/SMPTE 302M audio decoder
  aes3                  AES3/SMPTE 302M audio packetizer
  sdl_image             SDL_image video decoder
  twolame               Libtwolame audio encoder
  avcodec               FFmpeg audio/video decoder
  avcodec               FFmpeg deinterlace video filter
  avcodec               FFmpeg audio/video encoder
  vorbis                Vorbis audio decoder
  vorbis                Vorbis audio encoder
  vorbis                Vorbis audio packetizer
  lpcm                  Linear PCM audio decoder
  lpcm                  Linear PCM audio packetizer
  main                  main program
[0x9381154] main libvlc debug: opening config file (/home/doug/.config/vlc/vlcrc)
[0x9381154] main libvlc debug: writing plugins cache /home/doug/.cache/vlc/plugins-04041e.dat



```

---

### Post by cotcot on 2009-06-01
> **mc4man said:**
> Try vlc from the terminal with 
```
vlc --reset-config --reset-plugins-cache
```

Thanks a lot. This command solved my problem with vlc not able to play video after the second time I open a video file.

---

### Post by aloasi on 2009-06-01
i did what you told me but no luck i really don't know whats wrong. i downloaded a .tar file with vlc 1.0.0 rc2 but don't know how to install it. Thank You again.

---

### Post by aloasi on 2009-06-01
up

---

### Post by aloasi on 2009-06-03
up, still need help with vlc.

---

