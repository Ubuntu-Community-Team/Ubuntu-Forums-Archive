---
title: "avconv join video &amp; audio without reencoding -&gt; segfault"
date: 2014-10-19
forum: Multimedia Software
---

### Post by kaefert66014235 on 2014-10-19
Hi there. I'd like to join a video mp4 file and an audio m4a file together into an mp4 file that contains both stream.
And I'd like to do that using this command line (because a tool that I'd like to have working does it like that):
```
avconv -loglevel debug -y -i 'vid.mp4' -i 'audio.m4a' -c copy -map 0:v:0 -map 1:a:0 -shortest 'output.mp4'
```

The problem is, on my Linux Mint 17 deskop (Ubuntu 14.04) avconv segfaults:

```
$ avconv -loglevel debug -y -i 'vid.mp4' -i 'audio.m4a' -c copy -map 0:v:0 -map 1:a:0 -shortest 'output.mp4'
avconv version 9.16-6:9.16-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Aug 10 2014 18:16:02 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:9.16-0ubuntu0.14.04.1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avutil      configuration: --enable-gpl --enable-nonfree --enable-version3 --enable-shared --enable-avisynth --enable-avresample --enable-libx264 --enable-libvorbis --enable-libfaac --enable-libmp3lame
  avresample  configuration: --enable-gpl --enable-nonfree --enable-version3 --enable-shared --enable-avisynth --enable-avresample --enable-libx264 --enable-libvorbis --enable-libfaac --enable-libmp3lame
  swscale     configuration: --enable-gpl --enable-nonfree --enable-version3 --enable-shared --enable-avisynth --enable-avresample --enable-libx264 --enable-libvorbis --enable-libfaac --enable-libmp3lame
  libavutil     52.  3. 0 / 52. 92.101
  libavcodec    54. 35. 0 / 54. 35. 0
  libavformat   54. 20. 4 / 54. 20. 4
  libavdevice   53.  2. 0 / 53.  2. 0
  libavfilter    3.  3. 0 /  3.  3. 0
  libavresample  1.  0. 1 /  1.  3. 0
  libswscale     2.  1. 1 /  2.  6.100
Splitting the commandline.
Reading option '-loglevel' ... matched as option 'loglevel' (set libav* logging level) with argument 'debug'.
Reading option '-y' ... matched as option 'y' (overwrite output files) with argument '1'.
Reading option '-i' ... matched as input file with argument 'vid.mp4'.
Reading option '-i' ... matched as input file with argument 'audio.m4a'.
Reading option '-c' ... matched as option 'c' (codec name) with argument 'copy'.
Reading option '-map' ... matched as option 'map' (set input stream mapping) with argument '0:v:0'.
Reading option '-map' ... matched as option 'map' (set input stream mapping) with argument '1:a:0'.
Reading option '-shortest' ... matched as option 'shortest' (finish encoding within shortest input) with argument '1'.
Reading option 'output.mp4' ... matched as output file.
Finished splitting the commandline.
Parsing a group of options: global .
Applying option loglevel (set libav* logging level) with argument debug.
Applying option y (overwrite output files) with argument 1.
Successfully parsed a group of options.
Parsing a group of options: input file vid.mp4.
Successfully parsed a group of options.
Opening an input file: vid.mp4.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1bc5420] Probed with size=2048 and score=100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1bc5420] ISO: File Type Major Brand: dash
[h264 @ 0x1bc7aa0] no picture
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1bc5420] All info found
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'vid.mp4':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6avc1mp41
    creation_time   : 2013-10-08 02:09:46
  Duration: 00:01:10.16, start: 0.000000, bitrate: 812 kb/s
    Stream #0.0(und), 20, 1/90000: Video: h264 (Main), yuv420p, 854x480, 1/50, 810 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Metadata:
      creation_time   : 2013-10-08 02:09:46
Successfully openened the file.
Parsing a group of options: input file audio.m4a.
Successfully parsed a group of options.
Opening an input file: audio.m4a.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1bcbf20] Probed with size=2048 and score=100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1bcbf20] ISO: File Type Major Brand: dash
Segmentation fault
```

ffmpeg works like a charm with the same files:
```
$ ffmpeg -i "vid.mp4" -i "audio.m4a" -acodec copy -vcodec copy output.mp4
ffmpeg version N-64847-g265dadb Copyright (c) 2000-2014 the FFmpeg developers
  built on Jul 21 2014 18:30:07 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --enable-gpl --enable-nonfree --enable-version3 --enable-shared --enable-avisynth --enable-avresample --enable-libx264 --enable-libvorbis --enable-libfaac --enable-libmp3lame
  libavutil      52. 92.101 / 52. 92.101
  libavcodec     55. 69.100 / 55. 69.100
  libavformat    55. 48.101 / 55. 48.101
  libavdevice    55. 13.102 / 55. 13.102
  libavfilter     4. 11.102 /  4. 11.102
  libavresample   1.  3.  0 /  1.  3.  0
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
  libpostproc    52.  3.100 / 52.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'vid.mp4':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6avc1mp41
    creation_time   : 2013-10-08 02:09:46
  Duration: 00:01:10.16, start: 0.000000, bitrate: 812 kb/s
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p, 854x480, 810 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc (default)
    Metadata:
      creation_time   : 2013-10-08 02:09:46
      handler_name    : VideoHandler
Input #1, mov,mp4,m4a,3gp,3g2,mj2, from 'audio.m4a':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6mp41
    creation_time   : 2013-10-08 02:09:53
  Duration: 00:01:10.29, start: 0.000000, bitrate: 255 kb/s
    Stream #1:0(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 253 kb/s (default)
    Metadata:
      creation_time   : 2013-10-08 02:09:53
      handler_name    : SoundHandler
Output #0, mp4, to 'output.mp4':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6avc1mp41
    encoder         : Lavf55.48.101
    Stream #0:0(und): Video: h264 ([33][0][0][0] / 0x0021), yuv420p, 854x480, q=2-31, 810 kb/s, 25 fps, 90k tbn, 90k tbc (default)
    Metadata:
      creation_time   : 2013-10-08 02:09:46
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: aac ([64][0][0][0] / 0x0040), 44100 Hz, stereo, 253 kb/s (default)
    Metadata:
      creation_time   : 2013-10-08 02:09:53
      handler_name    : SoundHandler
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #1:0 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame= 1754 fps=0.0 q=-1.0 Lsize=    9169kB time=00:01:10.28 bitrate=1068.7kbits/s    
video:6940kB audio:2176kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.587120%
```

Is there an extra repository somewhere where someone maintains a good and working avconv build? Or is there someway to make the ubuntu repository maintainers fix their avconv build?

---

### Post by mc4man on 2014-10-19
Not that I'm a fan of libav but your 2 commands are different so what are you actually comparing
(if you were to remove the map stuff what happens with avconv?

---

### Post by kaefert66014235 on 2014-10-19
> **mc4man said:**
> ... (if you were to remove the map stuff what happens with avconv?

the same segmentation fault.


Yes I know those are different commands, just put the working ffmpeg line there too to give more information, to show that the files I wanna join can be joined and are not at fault.

---

### Post by FakeOutdoorsman on 2014-10-19
Why not just use ffmpeg? It works and avconv (at least that version) doesn't.

---

### Post by mc4man on 2014-10-19
> **FakeOutdoorsman said:**
> Why not just use ffmpeg? It works and avconv (at least that version) doesn't.
+1 

If you absolutely had to have an advanced libav that's possible. I've got libav11 for 14.04 but it's shared so affects other packages.
(or just build yourself a static libav, instr. are somewhere, maybe..

---

### Post by kaefert66014235 on 2014-10-20
> **FakeOutdoorsman said:**
> Why not just use ffmpeg? It works and avconv (at least that version) doesn't.
I'm not directly using avconv but have another tool that performs the task using avconv in the background, and I'd like to use that tool for convenience purposes.

> **mc4man said:**
> ... If you absolutely had to have an advanced libav that's possible. I've got libav11 for 14.04 but it's shared so affects other packages.
(or just build yourself a static libav, instr. are somewhere, maybe..
Well yes. I could compile it myself. I had hoped there was an easier way like a repository where someone has put the necessary packages for a working avconv, or maybe if I would dream big for an ubuntu repository maintainer to read my post and say to himself "oh, we got a badly built package there in our default repository, I should fix it"...

I know that the problem lies with the build and not with avconv itself, since I did build it myself on another system once and that made it work like expected.

---

### Post by mc4man on 2014-10-20
Unfortunately the premise you're making, "the problem lies with the build and not with avconv ' is wrong. There is nothing wrong with 14.04's libav build in this regard. Running your exact 1st. command fails on libav9, libav11, & ffmpeg 2.4.2 due to  improper map parameters
So can't see where providing a new [libav9]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") or [libav11]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6")  will matter much.
(- I mux .mp4 & .m4a all the time, never needed -map's

This does work here in an install with libav9 using adjusted -map's (to no real advantage
> avconv -loglevel debug -y -i '/home/doug/Desktop/test/input.mp4'  -i '/home/doug/Desktop/test/input.m4a'  -c copy -map 0:0:v:0:0 -map 1:0:a:0:1 -shortest 'output1.mp4'
[COLOR="#0000CD"]avconv version 9.16-6:9.16-0ubuntu0.14.04.1[/COLOR]+fdkaac, Copyright (c) 2000-2014 the Libav developers
  built on Aug 11 2014 23:12:18 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:9.16-0ubuntu0.14.04.1+fdkaac' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --enable-libfdk-aac --enable-nonfree --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil     52.  3. 0 / 52.  3. 0
  libavcodec    54. 35. 0 / 54. 35. 0
  libavformat   54. 20. 4 / 54. 20. 4
  libavdevice   53.  2. 0 / 53.  2. 0
  libavfilter    3.  3. 0 /  3.  3. 0
  libavresample  1.  0. 1 /  1.  0. 1
  libswscale     2.  1. 1 /  2.  1. 1
Splitting the commandline.
Reading option '-loglevel' ... matched as option 'loglevel' (set libav* logging level) with argument 'debug'.
Reading option '-y' ... matched as option 'y' (overwrite output files) with argument '1'.
Reading option '-i' ... matched as input file with argument '/home/doug/Desktop/test/input.mp4'.
Reading option '-i' ... matched as input file with argument '/home/doug/Desktop/test/input.m4a'.
Reading option '-c' ... matched as option 'c' (codec name) with argument 'copy'.
Reading option '-map' ... matched as option 'map' (set input stream mapping) with argument '0:0:v:0:0'.
Reading option '-map' ... matched as option 'map' (set input stream mapping) with argument '1:0:a:0:1'.
Reading option '-shortest' ... matched as option 'shortest' (finish encoding within shortest input) with argument '1'.
Reading option 'output1.mp4' ... matched as output file.
Finished splitting the commandline.
Parsing a group of options: global .
Applying option loglevel (set libav* logging level) with argument debug.
Applying option y (overwrite output files) with argument 1.
Successfully parsed a group of options.
Parsing a group of options: input file /home/doug/Desktop/test/input.mp4.
Successfully parsed a group of options.
Opening an input file: /home/doug/Desktop/test/input.mp4.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x220f7e0] Probed with size=2048 and score=100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x220f7e0] ISO: File Type Major Brand: dash
[h264 @ 0x2212500] no picture
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x220f7e0] All info found
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/doug/Desktop/test/input.mp4':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6avc1mp41
    creation_time   : 2014-03-10 10:40:36
  Duration: 00:04:07.47, start: 0.000000, bitrate: 2011 kb/s
    Stream #0.0(und), 20, 1/90000: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 1001/48000, 2009 kb/s, 23.98 fps, 23.97 tbr, 90k tbn, 47.95 tbc
    Metadata:
      creation_time   : 2014-03-10 10:40:36
Successfully openened the file.
Parsing a group of options: input file /home/doug/Desktop/test/input.m4a.
Successfully parsed a group of options.
Opening an input file: /home/doug/Desktop/test/input.m4a.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x2211000] Probed with size=2048 and score=100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x2211000] ISO: File Type Major Brand: dash
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x2211000] All info found
Input #1, mov,mp4,m4a,3gp,3g2,mj2, from '/home/doug/Desktop/test/input.m4a':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6mp41
    creation_time   : 2014-03-10 10:38:45
  Duration: 00:04:07.54, start: 0.000000, bitrate: 127 kb/s
    Stream #1.0(und), 1, 1/44100: Audio: aac, 44100 Hz, stereo, fltp, 125 kb/s
    Metadata:
      creation_time   : 2014-03-10 10:38:45
Successfully openened the file.
Parsing a group of options: output file output1.mp4.
Applying option c (codec name) with argument copy.
Applying option map (set input stream mapping) with argument 0:0:v:0:0.
Applying option map (set input stream mapping) with argument 1:0:a:0:1.
Applying option shortest (finish encoding within shortest input) with argument 1.
Successfully parsed a group of options.
Opening an output file: output1.mp4.
Successfully openened the file.
Output #0, mp4, to 'output1.mp4':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6avc1mp41
    creation_time   : 2014-03-10 10:40:36
    encoder         : Lavf54.20.4
    Stream #0.0(und), 0, 1/90000: Video: libx264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 1/90000, q=2-31, 2009 kb/s, 90k tbn, 90k tbc
    Metadata:
      creation_time   : 2014-03-10 10:40:36
    Stream #0.1(und), 0, 1/44100: Audio: libfdk_aac, 44100 Hz, stereo, 125 kb/s
    Metadata:
      creation_time   : 2014-03-10 10:38:45
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #1:0 -> #0:1 (copy)
Press ctrl-c to stop encoding
No more output streams to write to, finishing.
frame= 5934 fps=  0 q=-1.0 Lsize=   64647kB time=247.43 bitrate=2140.4kbits/s    
video:60694kB audio:3794kB global headers:0kB muxing overhead 0.246622%
doug@doug-Lenovo-IdeaPad-Y510P:~$ 

What is the name of your app that you wish to use?

---

### Post by kaefert66014235 on 2014-10-20
I didn't say that those map parameters are needed. It's just the command that this tool I'd like to use uses. And for me here if I leave out the mapping it also ends in a segmentation fault.

I'm not sure if it's a good idea to write the name of the tool here, since before posting a new thread I searched for and found other threads where the tool was mentioned which where closed / locked because that tool could be used to potentially break some laws or something. Therefore lets simply focus on avconv here.

So on that other (also linux mint 17 desktop) system I have built and installed libav11 myself and there the same command works like a charm. but its true it might simply be the difference between libav9 and libav11, not a problem with the build.

---

