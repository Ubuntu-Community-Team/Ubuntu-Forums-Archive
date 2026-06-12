---
title: "[SOLVED] I need to convert .WMV to .OGV!"
date: 2008-10-28
forum: Multimedia Software
---

### Post by Rytron on 2008-10-28
Hi,
I need to convert .WMV to .OGV!
What command line do I need to use in mencoder? Or should I use ffmpeg.
I want a conversion that keeps the sound and offers a minimum of quality loss.

Thanks.

---

### Post by FakeOutdoorsman on 2008-10-28
Theora video with FLAC audio:
```
ffmpeg -i hungryhungryhobos.wmv -sameq hungryhungryhobos.ogg
```
Theora video with vorbis audio:
```
ffmpeg -i hungryhungryhobos.wmv -sameq -acodec libvorbis hungryhungryhobos.ogg
```
You may need to use "-acodec vorbis" instead depending on how old your ffmpeg is.

---

### Post by Rytron on 2008-10-30
Hi,
The above code only got the audio. I also need the video with the audio.
The audio was very clear though.

---

### Post by FakeOutdoorsman on 2008-10-30
What version of Ubuntu are you using and where did you get ffmpeg (Ubuntu universe repo, Medibuntu, self-compiled)?  Can you paste the output of "ffmpeg -formats" and can you also paste the complete output ffmpeg gave you after you tried the commands?

---

### Post by gecka on 2008-10-30
If you are using Intrepid forget about format like AAC, XVID, etc...

At time of written there is no way to get support for such codecs in Intrepid.

Sure for most of us it is a regression but it is always like that with new Ubuntu distrib: lots of regressions.

Best regards.

---

### Post by Rytron on 2008-10-30
> **FakeOutdoorsman said:**
> What version of Ubuntu are you using and where did you get ffmpeg (Ubuntu universe repo, Medibuntu, self-compiled)?  Can you paste the output of "ffmpeg -formats" and can you also paste the complete output ffmpeg gave you after you tried the commands?

```
:~$ ffmpeg -formats
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
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


```
:~/Desktop$ ffmpeg -i a.wmv -sameq a.ogg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'a.wmv':
  Duration: 00:02:35.8, start: 2.000000, bitrate: 781 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 96 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 640x480, 25.00 fps(r)
Output #0, ogg, to 'a.ogg':
  Stream #0.0: Audio: vorbis, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=     510kB time=156.0 bitrate=  26.8kbits/s    
video:0kB audio:497kB global headers:3kB muxing overhead 1.976773%
```

```

:~/Desktop$ ffmpeg -i b.wmv -sameq -acodec libvorbis b.ogg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'b.wmv':
  Duration: 00:02:35.8, start: 2.000000, bitrate: 781 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 96 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 640x480, 25.00 fps(r)
Unknown codec 'libvorbis'
```


```
:~/Desktop$ ffmpeg -i b.wmv -sameq -acodec vorbis b.ogg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'b.wmv':
  Duration: 00:02:35.8, start: 2.000000, bitrate: 781 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 96 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 640x480, 25.00 fps(r)
Output #0, ogg, to 'b.ogg':
  Stream #0.0: Audio: vorbis, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=     510kB time=156.0 bitrate=  26.8kbits/s    
video:0kB audio:497kB global headers:3kB muxing overhead 1.976773%
```

---

### Post by FakeOutdoorsman on 2008-10-30
There are too many ffmpeg versions floating around with Ubuntu and it can even confuse a video nerd like me.  This should work, but I didn't test it:
```
ffmpeg -i b.wmv -sameq -vcodec libtheora -acodec vorbis -ab 96k b.ogg
```

---

### Post by Rytron on 2008-10-31
> **FakeOutdoorsman said:**
> There are too many ffmpeg versions floating around with Ubuntu and it can even confuse a video nerd like me.  This should work, but I didn't test it:
```
ffmpeg -i b.wmv -sameq -vcodec libtheora -acodec vorbis -ab 96k b.ogg
```

Here is the terminal output:
```

:~/Desktop$ ffmpeg -i b.wmv -sameq -vcodec libtheora -acodec vorbis -ab 96k b.ogg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'b.wmv':
  Duration: 00:02:35.8, start: 2.000000, bitrate: 781 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 96 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 640x480, 25.00 fps(r)
Output #0, ogg, to 'b.ogg':
  Stream #0.0: Video: libtheora, yuv420p, 640x480, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: vorbis, 44100 Hz, stereo, 96 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame= 3896 q=0.0 Lsize=   11563kB time=155.8 bitrate= 607.8kbits/s    
video:9896kB audio:497kB global headers:6kB muxing overhead 11.189741%
```


I tried differant players to play the b.ogg file but no luck.

Attached is the error I got when I tried Totem player.

---

### Post by mr_pouit on 2008-10-31
> **gecka said:**
> If you are using Intrepid forget about format like AAC, XVID, etc...

At time of written there is no way to get support for such codecs in Intrepid.

Sure for most of us it is a regression but it is always like that with new Ubuntu distrib: lots of regressions.

Best regards.

That's not true: an "unstripped" variant of ffmpeg is available in intrepid/multiverse, and supports AAC, XVID, H264...
You just need to install these libraries instead of the standard ffmpeg ones:
* libavcodec-unstripped-51
* libavdevice-unstripped-52
* libavformat-unstripped-52
* libavutil-unstripped-49
* libpostproc-unstripped-51
* libswscale-unstripped-0

Btw, many codec names seem to have changed since the old snapshot shipped in hardy (e.g. 'xvid' -> 'libxvid', 'aac' -> 'libfaac', 'h264' -> 'libx264', etc.).

---

### Post by FakeOutdoorsman on 2008-11-01
> **Rytron said:**
> 
I tried differant players to play the b.ogg file but no luck.

Attached is the error I got when I tried Totem player.
The ffmpeg output looks correct.  I'm not familiar with Totem.  Does it play with mplayer or vlc?

---

### Post by Rytron on 2008-11-01
Success!

I did a fresh install of Ubuntu 8.10.
Previously I was using Ubuntu 8.04.

The code:
```
ffmpeg -i b.wmv -sameq -vcodec libtheora -acodec vorbis -ab 96k b.ogg
```

now works perfectly.

Thanks to all.

---

