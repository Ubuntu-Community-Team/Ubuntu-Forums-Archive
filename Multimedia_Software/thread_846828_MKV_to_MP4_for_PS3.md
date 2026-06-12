---
title: "MKV to MP4 for PS3"
date: 2008-07-01
forum: Multimedia Software
---

### Post by digi691 on 2008-07-01
Most of this info was from hansa56 and edited for use with ffmpeg instead of the nerocodecs.  Let me know if this helps you.

First install mkvextract, mkvinfo, MP4Box, hexedit
$ sudo apt-get install mkvtoolnix gpac hexedit

I've downloaded Heroes Season 2 episode 11 which as this filename: Heroes_S02E11_720p.mkv (Just an example)

Then you have to find out which tracks contains the audio and video.
Run:
$ mkvinfo Heroes_S02E11_720p.mkv
Check out the printout to find the tracks.

(in my mkv file video is on track1 and audio is on track 2. Change the numbers to fit you mkv file)

Then demux the video from the mkvfile by running:
$ mkvextract tracks Heroes_S02E11_720p.mkv 1:video.h264

Next to do is to change one byte inside the video.h264.
$ hexedit video.h264
On the first line you should see this number combination:
"67 64 00 33"
change this to:
"67 64 00 29"
press ctrl-s to save and ctrl-x to exit

Then you need to convert audio to aac format using ffmpeg.
$ ffmpeg -i Heroes_S02E11_720p.mkv -vn -acodec mpeg4aac -ac 2 -ab 160k audio.m4a

This may take a couple of minutes.

The only thing left is to mux the video and audio file.  You need to make note of the fps the video is in from running mkvinfo.  Note down below you will see that this video is using 23.976.  If you do not put the correct values or leave this option out it will default to 25fps and your audio will be out of sync if the correct fps are not used.

$ MP4Box -fps 23.976 -add video.h264 -add audio.m4a Heroes_S02E11.mp4

All should be finished within 5 minutes because no video conversion is done.

Hans Audun
Rygge, Norway
(edited for use of ffmpeg by Chris D.)

Someone should be able to create a bash script for this process.

---

### Post by heiNey on 2009-01-27
thanks, was looking for a way to do this without neroencode

EDIT:hmmm....well, it doesnt seem to work...im not getting any sound :/ .  i can hear the .m4a file if i listen to it thru audacious, but after muxing and playing it on the ps3, there's only video.  (btw, had the same problem with neroencode)

---

### Post by digi691 on 2009-01-28
That is odd...  What version of the PS3 firmware are you running?

---

### Post by heiNey on 2009-01-30
system says 2.60, which is the latest i believe.

---

### Post by heiNey on 2009-02-04
found a solution...unfortunately, it required me going back to windows.

there's a program called GOTSent ([http://sentry23.googlepages.com/](http://sentry23.googlepages.com/)) that essentially does the same thing. i watched it do its thing and it rips the audio as an aac file instead of m4a.  but it still used mkvextract and mp4box to mux it together.  files work fine on my ps3 with this program though.

tried using it with wine, but it says it needs some dll's or something.  so if someone else cant figure it out with ubuntu, give this program a try.  it does batch encoding too.

---

### Post by wolfen69 on 2009-02-04
why not just use [Handbrake]("http://handbrake.fr/?article=download")? 1 click conversion to mp4.

---

### Post by AbstractZero on 2009-02-05
Hi,

Installing Handbrake wasn't easy, I'll give it a new try tomorrow.

I have a problem trying "MP4Box -splits 4000000 ..." and get an error message like this: "Error cloning track 1 sample 106".
Anyone got a solution to this problem?

---

### Post by digi691 on 2009-02-05
@heiNey

```
$ ffmpeg -i Heroes_S02E11_720p.mkv -vn -acodec mpeg4aac -ac 2 -ab 160k audio.m4a
```

The codec in that line uses mpeg4aac.  So there should be no difference.  The only thing I can think of is something in ffmpeg changed or your using the wrong package of ffmpeg. Unfortunately I cannot check what version I have installed because my HD crashed and haven't had time to figure out the issue.

---

### Post by AbstractZero on 2009-02-07
Hi,

Now I know why not to use HandBrake, it takes forever... ETA >24h. :(
What takes about 15 minutes the other way.
Besides that HandBrake is very nice.

---

### Post by heiNey on 2009-02-07
ill give that handbrake program a shot (EDIT: well, it looks like its made to encode stuff, while the above set of commands just changes the container, which is much faster than doing an encode of everything)

i did a apt-get install ffmpeg and it says its already the latest version

```

ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896

```

i copied and pasted the commands and just edited the input file.  so i dont think im doing anything wrong.

---

### Post by viikinki on 2009-02-13
I encountered following problem when converting video file:

MP4Box -add movie.h264 -add movie_6ch.aac movie_6ch.mp4
AVC-H264 import - frame size 1920 x 1080 at 25.000 FPS                                                     
Import results: 79318 samples - Slices: 1017 I 40411 P 37890 B - 80301 SEI - 983 IDR                       
*** buffer overflow detected ***: MP4Box terminated                                                        
======= Backtrace: =========                                                                               
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c2ad38]                                              
/lib/tls/i686/cmov/libc.so.6[0xb7c28e40]                                                                   
/usr/lib/libgpac-0.4.4.so(chpl_New+0x50)[0xb7db1cf0]                                                       
/usr/lib/libgpac-0.4.4.so(gf_isom_box_new+0x715)[0xb7dd0185]                                               
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_box+0x13d)[0xb7dd138d]                                             
/usr/lib/libgpac-0.4.4.so(udta_Read+0x60)[0xb7db2f40]                                                      
/usr/lib/libgpac-0.4.4.so(gf_isom_box_read+0xbd)[0xb7dccf5d]                                               
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_box+0x279)[0xb7dd14c9]                                             
/usr/lib/libgpac-0.4.4.so(gf_isom_read_box_list+0x3d)[0xb7dd197d]                                          
/usr/lib/libgpac-0.4.4.so(moov_Read+0x2e)[0xb7db429e]                                                      
/usr/lib/libgpac-0.4.4.so(gf_isom_box_read+0x977)[0xb7dcd817]                                              
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_box+0x279)[0xb7dd14c9]                                             
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_root_box+0x52)[0xb7dd1a62]                                         
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_movie_boxes+0x96)[0xb7dd8556]                                      
/usr/lib/libgpac-0.4.4.so(gf_isom_open_file+0xe7)[0xb7dd88f7]                                              
/usr/lib/libgpac-0.4.4.so(gf_isom_open+0x4f)[0xb7ddc83f]                                                   
/usr/lib/libgpac-0.4.4.so(gf_media_import+0xb0)[0xb7e548e0]                                                
MP4Box[0x8061f7f]                                                                                          
MP4Box[0x804ef28]                                                                                          
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7b43775]                                           
MP4Box[0x804cea1]                                                                                          
======= Memory map: ========                                                                               
08048000-0806f000 r-xp 00000000 08:01 139624     /usr/bin/MP4Box                                           
0806f000-08071000 r--p 00026000 08:01 139624     /usr/bin/MP4Box                                           
08071000-08072000 rw-p 00028000 08:01 139624     /usr/bin/MP4Box
099ab000-0a077000 rw-p 099ab000 00:00 0          [heap]
b77e9000-b7837000 rw-p b77e9000 00:00 0
b785e000-b78ac000 rw-p b785e000 00:00 0
b790a000-b7957000 rw-p b790a000 00:00 0
b7957000-b7959000 r-xp 00000000 08:01 5526       /lib/tls/i686/cmov/libdl-2.9.so
b7959000-b795a000 r--p 00001000 08:01 5526       /lib/tls/i686/cmov/libdl-2.9.so
b795a000-b795b000 rw-p 00002000 08:01 5526       /lib/tls/i686/cmov/libdl-2.9.so
b795b000-b795c000 rw-p b795b000 00:00 0
b795c000-b7971000 r-xp 00000000 08:01 5538       /lib/tls/i686/cmov/libpthread-2.9.so
b7971000-b7972000 r--p 00014000 08:01 5538       /lib/tls/i686/cmov/libpthread-2.9.so
b7972000-b7973000 rw-p 00015000 08:01 5538       /lib/tls/i686/cmov/libpthread-2.9.so
b7973000-b7975000 rw-p b7973000 00:00 0
b7975000-b7aa7000 r-xp 00000000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7aa7000-b7aa8000 ---p 00132000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7aa8000-b7ab0000 r--p 00132000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7ab0000-b7abd000 rw-p 0013a000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7abd000-b7ac1000 rw-p b7abd000 00:00 0
b7ac1000-b7b03000 r-xp 00000000 08:01 8397       /usr/lib/i686/cmov/libssl.so.0.9.8
b7b03000-b7b04000 r--p 00041000 08:01 8397       /usr/lib/i686/cmov/libssl.so.0.9.8
b7b04000-b7b07000 rw-p 00042000 08:01 8397       /usr/lib/i686/cmov/libssl.so.0.9.8
b7b07000-b7b2b000 r-xp 00000000 08:01 5527       /lib/tls/i686/cmov/libm-2.9.so
b7b2b000-b7b2c000 r--p 00023000 08:01 5527       /lib/tls/i686/cmov/libm-2.9.so
b7b2c000-b7b2d000 rw-p 00024000 08:01 5527       /lib/tls/i686/cmov/libm-2.9.so
b7b2d000-b7c89000 r-xp 00000000 08:01 5523       /lib/tls/i686/cmov/libc-2.9.so
b7c89000-b7c8b000 r--p 0015b000 08:01 5523       /lib/tls/i686/cmov/libc-2.9.so
b7c8b000-b7c8c000 rw-p 0015d000 08:01 5523       /lib/tls/i686/cmov/libc-2.9.so
b7c8c000-b7c90000 rw-p b7c8c000 00:00 0
b7c90000-b7ca4000 r-xp 00000000 08:01 4386       /usr/lib/libz.so.1.2.3.3
b7ca4000-b7ca6000 rw-p 00013000 08:01 4386       /usr/lib/libz.so.1.2.3.3
b7ca6000-b7f1f000 r-xp 00000000 08:01 139547     /usr/lib/libgpac-0.4.4.so
b7f1f000-b7f20000 r--p 00279000 08:01 139547     /usr/lib/libgpac-0.4.4.so
b7f20000-b7f24000 rw-p 0027a000 08:01 139547     /usr/lib/libgpac-0.4.4.so
b7f24000-b7f26000 rw-p b7f24000 00:00 0
b7f29000-b7f36000 r-xp 00000000 08:01 2264       /lib/libgcc_s.so.1
b7f36000-b7f37000 r--p 0000c000 08:01 2264       /lib/libgcc_s.so.1
b7f37000-b7f38000 rw-p 0000d000 08:01 2264       /lib/libgcc_s.so.1
b7f38000-b7f3d000 rw-p b7f38000 00:00 0
b7f3dAborted (core dumped)

This error does not tell me much. Any ideas?

---

### Post by viikinki on 2009-02-15
> **viikinki said:**
> I encountered following problem when converting video file:

MP4Box -add movie.h264 -add movie_6ch.aac movie_6ch.mp4
AVC-H264 import - frame size 1920 x 1080 at 25.000 FPS                                                     
Import results: 79318 samples - Slices: 1017 I 40411 P 37890 B - 80301 SEI - 983 IDR                       
*** buffer overflow detected ***: MP4Box terminated                                                        
======= Backtrace: =========                                                                               
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c2ad38]                                              
/lib/tls/i686/cmov/libc.so.6[0xb7c28e40]                                                                   
/usr/lib/libgpac-0.4.4.so(chpl_New+0x50)[0xb7db1cf0]                                                       
/usr/lib/libgpac-0.4.4.so(gf_isom_box_new+0x715)[0xb7dd0185]                                               
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_box+0x13d)[0xb7dd138d]                                             
/usr/lib/libgpac-0.4.4.so(udta_Read+0x60)[0xb7db2f40]                                                      
/usr/lib/libgpac-0.4.4.so(gf_isom_box_read+0xbd)[0xb7dccf5d]                                               
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_box+0x279)[0xb7dd14c9]                                             
/usr/lib/libgpac-0.4.4.so(gf_isom_read_box_list+0x3d)[0xb7dd197d]                                          
/usr/lib/libgpac-0.4.4.so(moov_Read+0x2e)[0xb7db429e]                                                      
/usr/lib/libgpac-0.4.4.so(gf_isom_box_read+0x977)[0xb7dcd817]                                              
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_box+0x279)[0xb7dd14c9]                                             
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_root_box+0x52)[0xb7dd1a62]                                         
/usr/lib/libgpac-0.4.4.so(gf_isom_parse_movie_boxes+0x96)[0xb7dd8556]                                      
/usr/lib/libgpac-0.4.4.so(gf_isom_open_file+0xe7)[0xb7dd88f7]                                              
/usr/lib/libgpac-0.4.4.so(gf_isom_open+0x4f)[0xb7ddc83f]                                                   
/usr/lib/libgpac-0.4.4.so(gf_media_import+0xb0)[0xb7e548e0]                                                
MP4Box[0x8061f7f]                                                                                          
MP4Box[0x804ef28]                                                                                          
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7b43775]                                           
MP4Box[0x804cea1]                                                                                          
======= Memory map: ========                                                                               
08048000-0806f000 r-xp 00000000 08:01 139624     /usr/bin/MP4Box                                           
0806f000-08071000 r--p 00026000 08:01 139624     /usr/bin/MP4Box                                           
08071000-08072000 rw-p 00028000 08:01 139624     /usr/bin/MP4Box
099ab000-0a077000 rw-p 099ab000 00:00 0          [heap]
b77e9000-b7837000 rw-p b77e9000 00:00 0
b785e000-b78ac000 rw-p b785e000 00:00 0
b790a000-b7957000 rw-p b790a000 00:00 0
b7957000-b7959000 r-xp 00000000 08:01 5526       /lib/tls/i686/cmov/libdl-2.9.so
b7959000-b795a000 r--p 00001000 08:01 5526       /lib/tls/i686/cmov/libdl-2.9.so
b795a000-b795b000 rw-p 00002000 08:01 5526       /lib/tls/i686/cmov/libdl-2.9.so
b795b000-b795c000 rw-p b795b000 00:00 0
b795c000-b7971000 r-xp 00000000 08:01 5538       /lib/tls/i686/cmov/libpthread-2.9.so
b7971000-b7972000 r--p 00014000 08:01 5538       /lib/tls/i686/cmov/libpthread-2.9.so
b7972000-b7973000 rw-p 00015000 08:01 5538       /lib/tls/i686/cmov/libpthread-2.9.so
b7973000-b7975000 rw-p b7973000 00:00 0
b7975000-b7aa7000 r-xp 00000000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7aa7000-b7aa8000 ---p 00132000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7aa8000-b7ab0000 r--p 00132000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7ab0000-b7abd000 rw-p 0013a000 08:01 8396       /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7abd000-b7ac1000 rw-p b7abd000 00:00 0
b7ac1000-b7b03000 r-xp 00000000 08:01 8397       /usr/lib/i686/cmov/libssl.so.0.9.8
b7b03000-b7b04000 r--p 00041000 08:01 8397       /usr/lib/i686/cmov/libssl.so.0.9.8
b7b04000-b7b07000 rw-p 00042000 08:01 8397       /usr/lib/i686/cmov/libssl.so.0.9.8
b7b07000-b7b2b000 r-xp 00000000 08:01 5527       /lib/tls/i686/cmov/libm-2.9.so
b7b2b000-b7b2c000 r--p 00023000 08:01 5527       /lib/tls/i686/cmov/libm-2.9.so
b7b2c000-b7b2d000 rw-p 00024000 08:01 5527       /lib/tls/i686/cmov/libm-2.9.so
b7b2d000-b7c89000 r-xp 00000000 08:01 5523       /lib/tls/i686/cmov/libc-2.9.so
b7c89000-b7c8b000 r--p 0015b000 08:01 5523       /lib/tls/i686/cmov/libc-2.9.so
b7c8b000-b7c8c000 rw-p 0015d000 08:01 5523       /lib/tls/i686/cmov/libc-2.9.so
b7c8c000-b7c90000 rw-p b7c8c000 00:00 0
b7c90000-b7ca4000 r-xp 00000000 08:01 4386       /usr/lib/libz.so.1.2.3.3
b7ca4000-b7ca6000 rw-p 00013000 08:01 4386       /usr/lib/libz.so.1.2.3.3
b7ca6000-b7f1f000 r-xp 00000000 08:01 139547     /usr/lib/libgpac-0.4.4.so
b7f1f000-b7f20000 r--p 00279000 08:01 139547     /usr/lib/libgpac-0.4.4.so
b7f20000-b7f24000 rw-p 0027a000 08:01 139547     /usr/lib/libgpac-0.4.4.so
b7f24000-b7f26000 rw-p b7f24000 00:00 0
b7f29000-b7f36000 r-xp 00000000 08:01 2264       /lib/libgcc_s.so.1
b7f36000-b7f37000 r--p 0000c000 08:01 2264       /lib/libgcc_s.so.1
b7f37000-b7f38000 rw-p 0000d000 08:01 2264       /lib/libgcc_s.so.1
b7f38000-b7f3d000 rw-p b7f38000 00:00 0
b7f3dAborted (core dumped)

This error does not tell me much. Any ideas?

This seems to audio related.

If I extract the audio file movie_6ch.aac from mkv file by using this:

neroAacEnc -ignorelength -q 0.30 -if audiodump.wav -of movie_6ch.aac &  mplayer movie.mkv -ac ffac3 -channels 6 -af format=s16le,channels=6:6:0:0:1:2:2:1:3:4:4:5:5:3 -vo null -vc null -ao pcm:fast:waveheader:file=audiodump.wav -novideo -quiet -nolirc

the error appers but on the other hand when I extract the audio file  movie_6ch.aac it like this:

faac -q 234 -o movie_6ch.aac -P -C 6 -X --mpeg-vers 4 audiodump.wav & mplayer movie.mkv -ac ffac3 -channels 6 -af format=s16le,channels=6:6:0:2:1:4:2:3:3:0:4:1:5:5 -vo null -vc null -ao pcm:fast:waveheader:file=audiodump.wav -novideo -quiet -nolirc

the audio works as planned. Not very good quality though

---

### Post by kedmond on 2010-03-28
> **digi691 said:**
> 
Then demux the video from the mkvfile by running:
$ mkvextract tracks Heroes_S02E11_720p.mkv 1:video.h264

Next to do is to change one byte inside the video.h264.
$ hexedit video.h264
On the first line you should see this number combination:
"67 64 00 33"
change this to:
"67 64 00 29"
press ctrl-s to save and ctrl-x to exit

Then you need to convert audio to aac format using ffmpeg.
$ ffmpeg -i Heroes_S02E11_720p.mkv -vn -acodec mpeg4aac -ac 2 -ab 160k audio.m4a

This may take a couple of minutes.

The only thing left is to mux the video and audio file.  You need to make note of the fps the video is in from running mkvinfo.  Note down below you will see that this video is using 23.976.  If you do not put the correct values or leave this option out it will default to 25fps and your audio will be out of sync if the correct fps are not used.

$ MP4Box -fps 23.976 -add video.h264 -add audio.m4a Heroes_S02E11.mp4




Hey, thanks for the instructions!  At first, I couldn't get the audio to work since the mpeg4aac encoder isn't used anymore.  If I replace that with libfaac, it works nicely.

While it's all excellent on my laptop, it doesn't work on my PS3.

The video is black, but the audio DOES work.  What could I be doing wrong with the video?  The original files are "x264" MKV files.  Thanks.

---

### Post by digi691 on 2010-03-29
I have been seen the same problem lately as well. So when you flip the byte from 33 to 29 you are changing the profile from 5.1 x264 encode to a 4.1. Technically you not actually changing the profile your just tricking the Ps3 into playingA 5.1 encode.  This wasn't a problem before but recently people started encoding the 5.1 profile with an 8 frame reference instead of a 4. The ps3 cannot play an x264 video stream with this and needs to see the 4frame reference hence why you see black. The only way to see if the x264 video frame reference is using mediainfo on the original mkv.  I just installed the windows version on wine. Right now I only think you can reencode :/. If your ordinal file x264 video stream is a 4.1 profile or a 5.1 profile with a 4 frame refernce it will work. If it's a 5.1 profile with a 8 frame reference I believe it will require a total reencode. Hopefully someone can prove me wrong.

---

### Post by FunkyRes on 2010-04-07
This is what I did in jaunty, though not for PS3 -

```

#!/bin/bash

base=`echo $1 |sed -e s?"\.mkv$"?""?`

vidTrack=`mkvinfo ${base}.mkv |grep "Track type" \
|grep -n "video" |cut -d":" -f1`
audTrack=`mkvinfo ${base}.mkv |grep "Track type" \
|grep -n "audio" |cut -d":" -f1`

mkvextract tracks ${base}.mkv ${vidTrack}:${base}.h264
mkvextract tracks ${base}.mkv ${audTrack}:${base}.ac3

a52dec -o wavdolby ${base}.ac3 > ${base}.wav
rm -f ${base}.ac3
normalize-audio ${base}.wav


ffmpeg -i ${base}.h264 -i ${base}.wav -map 0:0 -map 1:0 -vcodec copy \
-acodec libfaac -ab 128k -y -f mp4 ${base}.mp4

rm -f ${base}.h264 ${base}.wav

```

Unfortunately it isn't working in Karmic, instead it complains:

Unknown encoder 'libfaac'

So now I have to figure that out ...

It does dolby mkv to stereo mp4 and worked quite well (I don't have surround sound).

---

### Post by FunkyRes on 2010-04-07
My solution works again - I had to follow the "C. Mediabuntu" instructions at [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Then it still didn't work, I had to run ldconfig - why the smurf did I have to manually run ldconfig? That should automatically be run after the install of **any** shared library.

I know I had the mediabuntu repository installed and enabled in Jaunty, guess upgrading disabled some of my repos. That's broken, it should only disable repos that don't have current equivalents. I guess that's the last time I ever do a dist upgrade, this wasn't the only issue I had that broke with the dist upgrade. Ubuntu needs to fix that.

Anyway, the script I posted now works again.

Save it as something like mkv2mp4.sh and the first (and only) argument is the mkv file you want to convert to mp4 - IE

```

mkv2mp4.sh Stargate.Universe.S01E11.720p.HDTV.x264-SiTV.mkv

```

If you want to preserve surround sound, that's up to you to modify the script, but the basic principle is to extract the video and audio from the mkv into separate files. Then you can do whatever you need to do to the audio (I like to convert to stereo and normalize it) and then use ffmpeg to join them into an mp4 again - without needing to re-encode the video (which is bad as it reduces visual quality).

---

### Post by brk3 on 2010-11-18
Has anyone been able to play files done with this method on Xbox360?

Just tried there but get an unsupported media error..

---

