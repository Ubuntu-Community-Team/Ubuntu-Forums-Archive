---
title: "Batch conversion from .flv to .avi?"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by jamesbeat on 2008-04-06
I have a lot (over a hundred) .flv videos that I have downloaded from youtube et al, and I want to convert them to .avi to play in my car.
At the moment, I'm using this command:

ffmpeg -i name.flv -vcodec msmpeg4v2 -b 312k -mbd 2 name.avi

But obviously this is an incredibly laborious process to repeat for a large number of files.

Is there a way of processing them as a batch?

---

### Post by ubuntu-freak on 2008-04-06
Try WinFF from [www.biggmatt.com](www.biggmatt.com), it's a frontend for FFmpeg.
 
Nathan

---

### Post by jamesbeat on 2008-04-06
Ok, I've just tried winff, but I keep getting the error message: 'invalid floating point operation'

I'm afraid I'm a bit of a noob and I'm not really sure what to do

---

### Post by ron999 on 2008-04-06
Hi 
With Winff have you tested it with one flv file using the preset 'XVID in AVI (4:3)'?

---

### Post by jamesbeat on 2008-04-06
Yes, but I still get the error message.
It happens almost every time I click a button in the program, so something is clearly very wrong.

On another note, the last few files I converted run fine on mplayer, but when I put them onto my media player they don't play properly, It's as if they are being fast forwarded.
I'm guessing my player doesn't like the bitrate or something. Any ideas?

---

### Post by ron999 on 2008-04-06
Well, make sure Winff is installed correctly by trying to convert a different type of file, such as an mp3 audio file.

Winff has a built-in player. If the player won't play an audio or video file then it won't be able to convert it either.

Lastly, do some research on your media player. Find out about picture size, codecs, frame rate, bitrates etc.
:guitar:

---

### Post by jamesbeat on 2008-04-06
It will play the video and audio files, but when I try and set the output type before I convert, I get the error message. I just don't get it, the codecs are there otherwise the files wouldn't play at all.

My media player's instruction manual is in 'engrish', and just states that it will play MP1.2, PEG4, Divx, Xvid, VCD, DVD .avi etc, no info on bitrates or anything. I guess that's a question for another forum though.

---

### Post by ron999 on 2008-04-06
OK, start Winff.
Click on 'Convert to...'
Choose a preset such as XVID in AVI(4:3)
Then click on +Add
Then look in your files for an flv file and select it.
Then click 'Convert'.

That's how I do it.
:)

---

### Post by jamesbeat on 2008-04-06
It wouldn't even let me get that far!

I installed an older (stable) version, everything went ok, all dependencies satisfied.

I can now select to convert to AVI(4:3) and I can play the file, but when I click the 'convert' button, nothing happens!

If I have no files selected for conversion, I get a message asking me to select at least one file to convert, but when I do so, it just ignores me :(

---

### Post by ron999 on 2008-04-06
Right, I'm out of ideas.:confused:
Winff works ok for me when converting YouTube vids.

Maybe someone else will think of something.:(

---

### Post by jamesbeat on 2008-04-06
Ok, thanks for trying.
I tried completely removing it with synaptics package manager and reinstalling it, but the same thing happens :(

---

### Post by ubuntu-freak on 2008-04-06
I don't understand what's up. It's just a frontend for FFmpeg, which you have had success with yeah? Maybe your previous avi vids are different to the ones WinFF wants to make. Install the packages from part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and take a look at part 3 just to be sure. 
 
Nathan

---

### Post by jamesbeat on 2008-04-07
Aha! I'm getting closer...

I followed your instructions, and now when I click 'convert', something happens:
A terminal window pops up (this didn't happen before) and it runs a script. Unfortunately, I then get an error message stating:

'unable for find a suitable output format for AVI' 

(that's not a typo by the way, it does say 'unable *for* find')

---

### Post by ron999 on 2008-04-07
Yes, when Winff is doing a conversion it shows that terminal so you can see the progress.
It looks like it's working now. But maybe you have not got the correct codecs installed.
The codecs used for the XVID in AVI(4:3) option are xvid for the video and mp3 for the audio.

---

### Post by ubuntu-freak on 2008-04-07
Did you install the codecs from my how-to? The latest version of WinFF doesn't work for me either, but the older one does. 

Nathan

P.S. [Matt knows](http://winff.org/forums/index.php?topic=127.0) about the bug in the latest version, it's something to do with GTK2 and WinFF not playing nice together.

---

### Post by jamesbeat on 2008-04-07
Yes, I'm pretty sure I installed everything properly, and I can play xvid files.
I get a new error now: unknown codec 'xvid'
which is bizarre....

---

### Post by ubuntu-freak on 2008-04-07
> **jamesbeat said:**
> Yes, I'm pretty sure I installed everything properly, and I can play xvid files.
I get a new error now: unknown codec 'xvid'
which is bizarre....

 
You selected the MS Compatible avi yeah? That's how I made mine.
 
Nathan

---

### Post by cor2y on 2008-04-07
have you tried playing the flv files in ffplay?
The media player for ffmpeg, if they don't play then you may have to compile ffmpeg yourself to have the right decoders so it can convert and play the files, if that scares you then try playing the files in mplayer, if they work then you will have to use mencoder to do the conversion and to batch process use a script of some sort, i am sure there are several floating around for flv to avi using mencoder.
To play a file with ffplay via the terminal (there is no gui frontend i think) ```
 ffplay filename.flv
``` to see error messages, media info and such ```
 ffplay -stats file.flv
```

---

### Post by ubuntu-freak on 2008-04-08
As far as I know, the Medibuntu FFmpeg only lacks AMR support. 
 
Nathan

---

### Post by jamesbeat on 2008-04-08
Hmm, ffplay plays both .flv and .avi (xvid) fine.

I tried some of the other filetypes in winff and they converted ok, I just can't convert to anything useful (ie. xvid of some description)

---

### Post by jamesbeat on 2008-04-08
I tried the command ffmpeg -formats and this was the output:

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
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

I can't see xvid mentioned anywhere?!

---

### Post by ubuntu-freak on 2008-04-08
So basically, you could make the avi's via the commandline, but not with WinFF? I don't get it. I thought Xvid was a type of mpeg4, not avi. Will the MS avi not do? Or mp4? You can add your own options in WinFF to make whatever vid you were creating with the commandline anyway.
 
Nathan

---

### Post by cor2y on 2008-04-09
If you want xvid or x264 it has to be specifically compiled into ffmpeg for encoding output.
You can however do plain mpeg4 video using the lavc syntax.
Which is why most guides on converting flv to avi with ffmpeg use lavc mpeg4 and not xvid or x264 since by default its not part of ffmpeg's default installation.

---

