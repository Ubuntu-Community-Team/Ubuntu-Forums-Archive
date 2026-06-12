---
title: "ffmpeg to .flv quality issues"
date: 2011-06-24
forum: Multimedia Software
---

### Post by richie bee on 2011-06-24
I am using this simple command to convert to .flv

```
ffmpeg -i test.mp4  -sameq  -acodec libfacc  -s 480x320 test.flv
```

the sound is o.k. but not great how can I improve it,

I have seen somewhere that libfaac is not the best audio codec.

---

### Post by andrew.46 on 2011-06-24
Can you post the complete terminal output from your command?

---

### Post by richie bee on 2011-06-25
[SIZE="3"][link to playing test files]("http://wiziwiz.com/test.html")[/SIZE] :popcorn:

Code:
```
ffmpeg -i test.mp4  -sameq  -acodec libfaac  -s 480x320 test.flv
```

Output:
```
$ ffmpeg -i test.mp4  -sameq  -acodec libfacc  -s 480x320 test.flv
FFmpeg version 0.6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Dec  4 2010 15:35:31 with gcc 4.1.2 20080704 (Red Hat 4.1.2-48)
  configuration: --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --incdir=/usr/include --disable-avisynth --extra-cflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic -fPIC' --enable-avfilter --enable-avfilter-lavf --enable-libdirac --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-shared --enable-swscale --enable-vdpau --enable-version3 --enable-x11grab
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
  Duration: 00:01:57.36, start: 0.000000, bitrate: 2672 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 2513 kb/s, 30 fps, 30 tbr, 30k tbn, 60 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 157 kb/s
Unknown encoder 'libfacc'
[richie@web1 testing]$ ffmpeg -i test.mp4  -sameq  -acodec libfaac  -s 480x320 test.flv
FFmpeg version 0.6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Dec  4 2010 15:35:31 with gcc 4.1.2 20080704 (Red Hat 4.1.2-48)
  configuration: --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --incdir=/usr/include --disable-avisynth --extra-cflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic -fPIC' --enable-avfilter --enable-avfilter-lavf --enable-libdirac --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-shared --enable-swscale --enable-vdpau --enable-version3 --enable-x11grab
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
  Duration: 00:01:57.36, start: 0.000000, bitrate: 2672 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 2513 kb/s, 30 fps, 30 tbr, 30k tbn, 60 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 157 kb/s
Output #0, flv, to 'test.flv':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0(und): Video: flv, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 200 kb/s, 1k tbn, 30 tbc
    Stream #0.1(und): Audio: libfaac, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 3518 fps= 97 q=0.0 Lsize=   56871kB time=117.28 bitrate=3972.3kbits/s dup=0 drop=1
video:55815kB audio:917kB global headers:0kB muxing overhead 0.245238%
```

thanks for looking (listening)

---

### Post by andrew.46 on 2011-06-25
Thanks for posting the details. Your existing mp4 contains h.264 video and aac sound, both of which live quite happily an an flv container. So perhaps in this case all that is required is:

```
ffmpeg -i test.mp4 -acodec copy -vcodec copy test.flv
```

Perhaps this will be enough?

---

### Post by richie bee on 2011-06-25
thanks for the response 

I should explain I am trying to perfect this to convert most file types with good quality,

I had tried -acopy and works fine for .mp4 but for a test.mpg didn't work...

---

### Post by FakeOutdoorsman on 2011-06-25
> **richie bee said:**
> I should explain I am trying to perfect this to convert most file types with good quality

More information would be useful to give example commands more suited for what you want. Why flv? What are using these output files for? I'm assuming you're going to be using them on a web site with a Flash player such as JW Player of Flowplayer, but I can only guess.

---

### Post by richie bee on 2011-06-25
Hi,

good question - the .flv format is for a videosite using latest jwplayer  - the idea being that the files have low file sizes equal or lower than the original but still retaining good quality for good streaming speeds, (served by a cnd)

we are also encoding 2 versions in .mp4 for ipod and a higher res for ipad that is not a problem.

but surely tweeking the flash is possible 

I have seen some of your other posts and even if it takes a more complex command code I am prepared to go down that path.

---

### Post by FakeOutdoorsman on 2011-06-25
> **richie bee said:**
> we are also encoding 2 versions in .mp4 for ipod and a higher res for ipad that is not a problem.
How are you encoding the iPod and iPad videos? Can you show your commands? JW Player can handle H.264 in .mp4, so perhaps you can use the iPod or iPad video as the web video too.

I once encoded videos for a client that wanted their videos online using JW Player and a downloadable version that worked on iPod. I just made one output per video that satisfied both requirements instead of making several versions, but your requirements may be different.

---

### Post by richie bee on 2011-06-25
You are right my requirements are different,

I notice also that vimeo.com have chosen the .mp4 route and html5 video also requires multiple format - but then why do the majority youtube.com still use .flv?

---

### Post by FakeOutdoorsman on 2011-06-26
Most YouTube videos I encounter these days are in the MP4 container, and the [Wikipedia entry on Youtube](http://en.wikipedia.org/wiki/Youtube#Quality_and_codecs) seems to support that assumption.

---

### Post by richie bee on 2011-06-28
O.k. you are right - looks like they have moved towards .mp4

staying on .flv I have tweeked my .flv conversion to something I am quite happy with,

```
ffmpeg -i test.mp4  -vcodec libx264 -vpre fast   -crf 26 -acodec libfaac -ab 256k -ar 48000  tues2.flv
```

however I have not set a width or height as I want to convert all types of sizes and keep their aspect ratio...

however I do want to scale them to about 720 px how do i go about doing this with ffmpeg?

---

### Post by FakeOutdoorsman on 2011-06-28
> **richie bee said:**
> however I do want to scale them to about 720 px how do i go about doing this with ffmpeg?

The best way to do this would be with the scale filter in FFmpeg. Unfortunately, as of Natty, the repository FFmpeg does not include filters (at least last time I checked), so you will have to compile FFmpeg to gain this functionality. Here are some easy to follow instructions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Your command will need to be updated because the syntax has changed when using libx264 with a newer FFmpeg, and because you can now use *scale*. By "720" I assume you mean height?
```
ffmpeg -i test.mp4 -vcodec libx264 -preset fast -crf 26 -threads 0 -vf scale="trunc(oh*a*2)/2:720" -acodec libfaac -aq 100 tues2.flv
```
This should scale everything to be 720 pixels high while (mostly) preserving the aspect ratio. The output width will vary depending on the width of the input. I also added *-threads 0* which will tell libx264 to use an appropriate value of "threads" for your CPU and will decrease the encoding time. I changed *-ab 256k* to *-aq 100* which I assume is the equivalent of *faac -q 100* and should end up being variable bitrate (VBR) audio.

Depending on your flash player, you may need to run the FFmpeg output through flvtool++, flvtool2, flvmeta, or any other similar tool (otherwise the player may not show a correct duration or may not even play it). I'm not sure how important this step is these days since I never use flv.

---

### Post by richie bee on 2011-06-28
thanks for that, glad there is a solution...

so my install FFmpeg version 0.6.1 won't cut it for the scaling feature?

I am going for a 720 width for web

---

### Post by FakeOutdoorsman on 2011-06-28
> **richie bee said:**
> so my install FFmpeg version 0.6.1 won't cut it for the scaling feature?
No.

> **richie bee said:**
> I am going for a 720 width for web
That's important information. If you want this then your command will change:
```
scale="720:trunc(ow/a/2)*2"
```

---

### Post by richie bee on 2011-06-28
I understand ffmpeg has gone through some big changes in the past 6 months so if I am upgrading is it any different to those instructions from 2008 in your link?

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by FakeOutdoorsman on 2011-06-28
If you scroll down to the bottom of the post you'll see "Last edited by FakeOutdoorsman; 5 Days Ago at 05:11 PM".

---

### Post by richie bee on 2011-06-28
wow that's a long thread impressive...

so the latest is called "love" [http://www.ffmpeg.org/download.html#release_0.8](http://www.ffmpeg.org/download.html#release_0.8)
 maybe they named it that as they have had a bit of falling out internally lately.

---

### Post by richie bee on 2011-06-29
O.k. I am upgrading to latest ffmpeg and will test,

do you know a good place to grab some test files in different formats,?

mov,wmv,mp4,mpg, etc

---

### Post by andrew.46 on 2011-06-29
> **richie bee said:**
> do you know a good place to grab some test files in different formats,?

mov,wmv,mp4,mpg, etc

The definitive collection:

[http://samples.mplayerhq.hu/](http://samples.mplayerhq.hu/)

---

### Post by richie bee on 2011-06-29
wow thanks 

there some weird ones out there and so many!:shock:

---

### Post by andrew.46 on 2011-06-29
Indeed! Just remember that some of these are broken files put there for testing but it is still a huuuuuuuge collection of very useful media files.

---

### Post by richie bee on 2011-06-29
I'm struggling to get ffmpeg-php to compile. I've tried the release version of 0.8 and the svn version, but I'm getting the following errors:

Any ideas?


```
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:74: error: 'MAX_STREAMS' undeclared here (not in a function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_video_stream':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:154: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:154: error: (Each undeclared identifier is reported only once
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:154: error: for each function it appears in.)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_audio_stream':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:167: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_open_movie_file':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:260: warning: 'av_open_input_file' is deprecated (declared at /usr/include/libavformat/avformat.h:1086)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_decoder_context':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:486: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getComment':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:533: error: 'AVFormatContext' has no member named 'comment'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:533: error: 'AVFormatContext' has no member named 'comment'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getTitle':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:548: error: 'AVFormatContext' has no member named 'title'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:548: error: 'AVFormatContext' has no member named 'title'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getAuthor':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:563: error: 'AVFormatContext' has no member named 'author'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:563: error: 'AVFormatContext' has no member named 'author'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getCopyright':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:577: error: 'AVFormatContext' has no member named 'copyright'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:577: error: 'AVFormatContext' has no member named 'copyright'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getAlbum':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:592: error: 'AVFormatContext' has no member named 'album'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:592: error: 'AVFormatContext' has no member named 'album'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getGenre':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:606: error: 'AVFormatContext' has no member named 'genre'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:606: error: 'AVFormatContext' has no member named 'genre'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getTrackNumber':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:621: error: 'AVFormatContext' has no member named 'track'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getYear':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:634: error: 'AVFormatContext' has no member named 'year'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_framerate':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:680: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_framenumber':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:812: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_pixelformat':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:852: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getPixelFormat':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:870: warning: 'avcodec_get_pix_fmt_name' is deprecated (declared at /usr/include/libavcodec/avcodec.h:3406)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_codec_name':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:965: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getVideoCodec':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:991: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getAudioCodec':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1011: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getVideoStreamId':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1031: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getAudioStreamId':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1053: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getAudioChannels':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1091: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getAudioSampleRate':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1127: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getAudioBitRate':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1163: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function 'zim_ffmpeg_movie_getVideoBitRate':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1183: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_read_av_frame':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1206: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1217: warning: implicit declaration of function 'avcodec_decode_video'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1221: error: 'PKT_FLAG_KEY' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_av_frame':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1248: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1284: error: 'AVCodecContext' has no member named 'hurry_up'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1286: error: 'AVCodecContext' has no member named 'hurry_up'
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c: In function '_php_get_sample_aspect_ratio':
/root/ffmpeg-php/ffmpeg-php/trunk/ffmpeg-php/ffmpeg_movie.c:1445: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
make: *** [ffmpeg_movie.lo] Error 1
```

---

### Post by FakeOutdoorsman on 2011-06-29
Sorry. I've never used ffmpeg-php. Just so you know, it's not an official FFmpeg project, so you won't get any help at #ffmpeg or the ffmpeg-user mailing list.

---

### Post by richie bee on 2011-06-29
O.k. a friend think he has fixed ffmpeg-php for me

Back to the video -

I have just tested the new command you suggested

```
ffmpeg -i test.mov -vcodec libx264 -preset fast -crf 23 -threads 0 -vf scale=\"720:trunc(ow/a/2)*2\" -acodec libfaac -aq 100 test.flv
```

looks good however the sound is bad - what I could only describe as slipping form fast to normal trying to keep up with the video...

---

### Post by FakeOutdoorsman on 2011-06-29
> **richie bee said:**
> looks good however the sound is bad - what I could only describe as slipping form fast to normal trying to keep up with the video...

With what player? Your flash one on the web site? Does it play as expected with ffplay?
```
ffplay input.flv
```

---

### Post by richie bee on 2011-06-29
I dont have ffplay 

I am testing on the web with jwplayer latest version

---

### Post by richie bee on 2011-06-29
tried again and got this
```
$ ffmpeg -i VID.mov -vcodec libx264 -preset fast -crf 23 -threads 0 -vf scale=\"720:trunc(ow/a/2)*2\" -acodec libfaac -aq 100 test.flv
-bash: syntax error near unexpected token `('
```

---

### Post by FakeOutdoorsman on 2011-06-29
Remove the backslashes:
```
scale="720:trunc(ow/a/2)*2"
```

---

### Post by richie bee on 2011-06-30
O.K. that works,

still got that "slipping" sound issue though -sort of breaking up trying to catch up...just a bit.

its the same in different players.

```
ffmpeg -i VID.mov -vcodec libx264 -preset fast -crf 23 -threads 0 -vf scale="720:trunc(ow/a/2)*2" -acodec libfaac -aq 100 wed4.flv
ffmpeg version 0.8, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 29 2011 13:47:11 with gcc 4.1.2 20080704 (Red Hat 4.1.2-50)
  configuration: --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --incdir=/usr/include --enable-shared --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-x11grab --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libfaac --enable-libmp3lame --enable-libopenjpeg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-swscale
  libavutil    51.  9. 1 / 51.  9. 1
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  4. 0 / 53.  4. 0
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 23. 0 /  2. 23. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1e151400] max_analyze_duration 5000000 reached at 5013333

Seems stream 0 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'VID.mov':
  Metadata:
    major_brand     : qt
    minor_version   : 537199360
    compatible_brands: qt
    creation_time   : 2011-06-29 20:36:34
  Duration: 00:01:39.37, start: 0.000000, bitrate: 17989 kb/s
    Stream #0.0(eng): Video: h264 (Main), yuv420p, 1440x1080, 17672 kb/s, PAR 4:3 DAR 16:9, 25 fps, 25 tbr, 2500 tbn, 5k tbc
    Metadata:
      creation_time   : 2011-06-29 20:36:34
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 313 kb/s
    Metadata:
      creation_time   : 2011-06-29 20:36:34
    Stream #0.2(eng): Data: tmcd / 0x64636D74
    Metadata:
      creation_time   : 2011-06-29 20:36:34
[buffer @ 0x1e1758e0] w:1440 h:1080 pixfmt:yuv420p tb:1/1000000 sar:4/3 sws_param:
[scale @ 0x1e196fa0] w:1440 h:1080 fmt:yuv420p -> w:720 h:538 fmt:yuv420p flags:0x4
[libx264 @ 0x1e158420] using SAR=4/3
[libx264 @ 0x1e158420] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x1e158420] profile High, level 3.0
[libx264 @ 0x1e158420] 264 - core 115 r2008 4c552d8 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=1 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, flv, to 'wed4.flv':
  Metadata:
    major_brand     : qt
    minor_version   : 537199360
    compatible_brands: qt
    creation_time   : 2011-06-29 20:36:34
    encoder         : Lavf53.4.0
    Stream #0.0(eng): Video: libx264, yuv420p, 720x538 [PAR 4:3 DAR 480:269], q=2-31, 200 kb/s, 1k tbn, 25 tbc
    Metadata:
      creation_time   : 2011-06-29 20:36:34
    Stream #0.1(eng): Audio: libfaac, 48000 Hz, stereo, s16, 64 kb/s
    Metadata:
      creation_time   : 2011-06-29 20:36:34
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop, [?] for help
frame= 2484 fps= 50 q=-1.0 Lsize=   14920kB time=00:01:39.28 bitrate=1231.1kbits/s
video:12999kB audio:1795kB global headers:0kB muxing overhead 0.853988%
frame I:59    Avg QP:20.53  size: 22467
[libx264 @ 0x1e158420] frame P:1676  Avg QP:24.42  size:  6453
[libx264 @ 0x1e158420] frame B:749   Avg QP:27.24  size:  1561
[libx264 @ 0x1e158420] consecutive B-frames: 54.1% 14.7%  6.6% 24.5%
[libx264 @ 0x1e158420] mb I  I16..4: 20.2% 61.2% 18.6%
[libx264 @ 0x1e158420] mb P  I16..4:  6.8% 11.7%  2.1%  P16..4: 23.9%  9.7%  4.3%  0.0%  0.0%    skip:41.4%
[libx264 @ 0x1e158420] mb B  I16..4:  1.0%  1.9%  0.4%  B16..8: 10.6%  3.8%  0.5%  direct: 5.0%  skip:76.9%  L0:36.5% L1:49.8% BI:13.7%
[libx264 @ 0x1e158420] 8x8 transform intra:57.3% inter:72.4%
[libx264 @ 0x1e158420] coded y,uvDC,uvAC intra: 47.8% 54.1% 20.0% inter: 13.8% 13.4% 1.2%
[libx264 @ 0x1e158420] i16 v,h,dc,p: 34% 43%  4% 19%
[libx264 @ 0x1e158420] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 19% 20% 21%  5%  7%  7%  7%  6%  7%
[libx264 @ 0x1e158420] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 24% 23% 16%  5%  8%  7%  7%  5%  5%
[libx264 @ 0x1e158420] i8c dc,h,v,p: 57% 20% 16%  7%
[libx264 @ 0x1e158420] Weighted P-Frames: Y:2.0% UV:1.4%
[libx264 @ 0x1e158420] ref P L0: 83.1% 16.9%
[libx264 @ 0x1e158420] ref B L0: 88.8% 11.2%
[libx264 @ 0x1e158420] ref B L1: 97.6%  2.4%
[libx264 @ 0x1e158420] kb/s:1071.65

```

---

### Post by richie bee on 2011-06-30
I think that -aq is only for libmp3lame (vbr mp3, values 1-9, where 9 is highest compression). FFmpeg says...
Code:
-aq quality         set audio quality (codec-specific)
For aac do I need other settings?

---

### Post by FakeOutdoorsman on 2011-06-30
> **richie bee said:**
> I dont have ffplay
FFplay should be built if you followed the compile instructions or if you use FFmpeg from the repository. Did you compile this on a headless machine or omit the sdl dependency?

> **richie bee said:**
> still got that "slipping" sound issue though -sort of breaking up trying to catch up...just a bit.
It's hard to say what is going on. Do you have a sample you can provide? Did you try flvtool++ or any of the other flv metadata tools I mentioned? Perhaps a different audio encoder will have better results:
```
ffmpeg -i VID.mov -vcodec libx264 -preset fast -crf 23 -threads 0 -vf scale="720:trunc(ow/a/2)*2" -acodec libmp3lame -aq 5 -ar 44100 wed4.flv
```

Or maybe .mp4 as the output container will perform as expected:
```
$ ffmpeg -i VID.mov -vcodec libx264 -preset fast -crf 23 -threads 0 -vf scale="720:trunc(ow/a/2)*2" -acodec libfaac -aq 100 wed4.mp4
$ qt-faststart wed4.mp4 output.mp4
```
qt-faststart will re-arrange some data in the .mp4 so the video can begin to play before it is completely downloaded, otherwise the whole video must download before it will start playing in the flash player.

> **richie bee said:**
> its the same in different players.
Which different players?

> **richie bee said:**
> I think that -aq is only for libmp3lame (vbr mp3, values 1-9, where 9 is highest compression). FFmpeg says...
Code:
-aq quality         set audio quality (codec-specific)
For aac do I need other settings?

You can use -aq with libfaac too, but the values differ between encoders. -aq 100 should be similar to "faac -q 100", an -aq 5 should be similar to "lame -V 5". See "man faac" and "man lame" for more info on those options and values.

---

### Post by richie bee on 2011-06-30
libmp3lame fixed it thanks

---

### Post by richie bee on 2011-07-01
I now have a new issue since upgrading to ffmpeg 8

my iphone command dosen't work now because of libfaac 

```
ffmpeg -i *INPUT FILE* -vcodec libx264 -vpre hq -vpre ipod640 -b 250k -bt 50k -acodec libfaac -ab 56k -ac 2 -s 480x320 *OUTPUT FILE*.mp4"
```

---

### Post by FakeOutdoorsman on 2011-07-01
Please provide enough information that the problem can be duplicated by others. By "doesn't work" do you mean FFmpeg isn't working, or the iPhone isn't working, or something else? Any actual errors you are receiving would be useful to know.

---

### Post by richie bee on 2011-07-01
the video was outputted but was really small and not even a second long

the error was -vpre hq not recognised so took it out

```
ffmpeg -i  VID.mov -vcodec libx264 -vpre ipod640 -b 250k -bt 50k -acodec libfaac -ab 56k -ac 2 -s 480x320 iphone.mp4
```

now it is converting but the video quality is bad and resized and no audio. 

so really need to start again from scratch and do this properly.

would like to use the libx264 scaling... however open to recommendations

would really appreciate it if you could suggest a better command for good iphone .mp4conversion

---

### Post by FakeOutdoorsman on 2011-07-01
> **richie bee said:**
> I now have a new issue since upgrading to ffmpeg 8
I assumed you followed this guide: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095).

This provides FFmpeg from Git, and not FFmpeg 0.8 as you say you're using. Are you even using Ubuntu? I saw "Red Hat" in one of your previous posts.

> **richie bee said:**
> the video was outputted but was really small and not even a second long

the error was -vpre hq not recognised so took it out

```
ffmpeg -i  VID.mov -vcodec libx264 -vpre ipod640 -b 250k -bt 50k -acodec libfaac -ab 56k -ac 2 -s 480x320 iphone.mp4
```

now it is converting but the video quality is bad and resized and no audio.
When you are having problems with FFmpeg, always show the complete terminal output with your FFmpeg command. The FFmpeg output provides useful information. Otherwise, I would have to guess what your issues are.

> **richie bee said:**
> would like to use the libx264 scaling... however open to recommendations
Do my previous scale examples not work for you?

> **richie bee said:**
> would really appreciate it if you could suggest a better command for good iphone .mp4conversion
I don't own an iDevice to test with so my suggestions may not work for you.

---

