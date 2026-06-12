---
title: "SMplayer Version of MPlayer doesn't support AAC?"
date: 2012-05-09
forum: Multimedia Software
---

### Post by ewangr on 2012-05-09
Here's the log I get from one of several files I'm having this problem with - exact same files play under VLC or under Windows, but to get smooth 1080 I need the vpau support so...

Setup is 64-bit Ubuntu 12.04 with the latest version of SMplayer installed:

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 56623149 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/ewang/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -nocache -osdlevel 0 -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/USB2_4TB/ForWatching/[Commie] Macross Frontier the Movie ~Sayonara no Tsubasa~ [BD 1080p AAC] [66AE8F11].mkv

MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/USB2_4TB/ForWatching/[Commie] Macross Frontier the Movie ~Sayonara no Tsubasa~ [BD 1080p AAC] [66AE8F11].mkv.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
Configuration: --extra-version='4:0.8.1-0ubuntu1' --arch=amd64 --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
libavformat file format detected.
[matroska,webm @ 0x7fa60464d940]max_analyze_duration reached
[matroska,webm @ 0x7fa60464d940]Estimating duration from bitrate, this may be inaccurate
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
[lavf] stream 1: audio (aac), -aid 0
ID_SUBTITLE_ID=0
[lavf] stream 2: subtitle (***), -sid 0
VIDEO:  [H264]  1916x1076  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in /media/USB2_4TB/ForWatching/
ID_FILENAME=/media/USB2_4TB/ForWatching/[Commie] Macross Frontier the Movie ~Sayonara no Tsubasa~ [BD 1080p AAC] [66AE8F11].mkv
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1916
ID_VIDEO_HEIGHT=1076
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7807
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_START_TIME=0.00
ID_LENGTH=6861.63
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [*** auto=1]
Couldn't open video filter '***'.
***: cannot add video filter
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
ID_VIDEO_CODEC=ffh264vdpau
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 0.0 kbit/0.00% (ratio: 0->576000)
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffaac
Starting playback...


MPlayer interrupted by signal 11 in module: decode video
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by andrew.46 on 2012-05-10
Perhaps update your version of MPlayer:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

---

### Post by ewangr on 2012-05-11
Followed the guide but the build of MPlayer dies with the following error:

libavformat/sctp.c:41:26: fatal error: netinet/sctp.h: No such file or directory
compilation terminated.
make[1]: *** [libavformat/sctp.o] Error 1
make[1]: Leaving directory `/home/ewang/mplayer_build/mplayer/ffmpeg'
make: *** [ffmpeg/libavformat/libavformat.a] Error 2


Any other suggestions?

---

### Post by andrew.46 on 2012-05-11
There is a breakage in MPlayer compilation at the moment, wait a day and try again :).

---

### Post by papibe on 2012-05-11
@andrew.46

Doesn't mplayer use ffmpeg codecs in the background?
and if so, wouldn't adding AAC support to ffmpeg solve this problem (like [this]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+aac") for example)?

:( Not sure myself, that's why I'm asking.
Regards.

---

### Post by andrew.46 on 2012-05-11
Might be a better option as compiling the svn version is broken :(.

---

### Post by cuyo01 on 2012-05-12
I use this ppa:
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

install mplayer2 since the latest normal mplayer build in this ppa is broken, the mplayer2 in this ppa works fine, its not the same that is in the mplayer2 homepage wich for me dont read dvd's

remember I found it through the mplayer homepage but not remember how, checked again and cant find it, also remember that in the mplayer homepage said that mplayer was compiled twice in a week in this ppa, so deactivate it if you dont want frequent updates, i do a update almost every 2 months activating the ppa and deactivating it again.

---

### Post by ewangr on 2012-05-12
Followed the instructions to build the FFMpeg, and now I have AAC support, but I still get an Error Code 1 because of mplyer not supporting A** subtitles. So guess I'm SOL until th mplayer build problem is fixed. Any idea when that might be? IOW when you say wait a day or so, do you mean today, or Monday, or... I'm just wondering if there is a weekly build where they make sure it works. Along that same line, would it be possible to just point the mplayer build to a different leg of the repository to just build the last "good" version rather than the nightly? Or would you have to change a lot of the other commands as well?

Thanks for the help!

---

### Post by PolyphemusNL on 2012-05-12
I did a:

```
sudo apt-get install libsctp-dev lksctp-tools
```

...and now it compiles :)

---

### Post by SeijiSensei on 2012-05-12
On the subbing group's site we have this:

> EVERY SINGLE ONE OF OUR RELEASES SINCE SEPTEMBER 7TH, 2011 IS 10 BIT.

**You cannot play a 10-bit encoding with VDPAU** because the H.264 decoder on the video card doesn't have support for 10-bit color.  Try playing it with the xv driver (in SMPlayer Options > Preferences > Video).  If your CPU can't keep up with a 1080p H.264 encode, then get a different version of the video.  

I just rebuilt mplayer2 from the source code at [http://www.mplayer2.org/](http://www.mplayer2.org/) the other day without incident.  You'll need to run

```
sudo apt-get install build-essential
sudo apt-get build-dep mplayer

```

to get the necessary compiler, headers and libraries.  After that it should build cleanly just by running "make" after you unpack the archive.

---

### Post by ewangr on 2012-05-12
Installed the additional libraries and was able to successfully build MPlayer, but then still getting the error code when I try to play the file.

If I use XV in SMplayer it plays the file, but there are no subtitles and it is jerky - just like VLC (except VLC does show the subtitles) since the ION2 really needs the vdpau libraries to use the hardware assist. However I think the "real" problem may be in how the embedded subtitles are handled. I ran the file from the command line and got:

```

MPlayer SVN-r34894-4.6 (C) 2000-2012 MPlayer Team

Playing [Commie] Macross Frontier the Movie ~Sayonara no Tsubasa~ [BD 1080p AAC] [66AE8F11].mkv.
libavformat version 54.4.100 (internal)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0
[lavf] stream 2: subtitle (***), -sid 0
VIDEO:  [H264]  1916x1076  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 creation_time: 2011-10-28 08:44:54
Load subtitles in ./
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.21.101 (internal)
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 0.0 kbit/0.00% (ratio: 0->576000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0xf217e0]using unscaled yuv420p10le -> yuv420p special converter
VO: [vdpau] 1916x1076 => 1916x1076 Planar YV12 

Subtitle word ',,' too long!

Subtitle word '' too long!

Subtitle word ',,' too long!

Subtitle word '' too long!

Subtitle word ',,' too long!

Subtitle word '' too long!

Subtitle word ',,' too long!

Subtitle word '' too long!

Subtitle word ',,' too long!

Subtitle word '' too long!
A:   0.2 V:   0.0 A-V:  0.201 ct:  0.004   0/  0 ??% ??% ??,?% 1 0 

Subtitle word ',,' too long!

Subtitle word ',,' too long!

Subtitle word ',,' too long!

Subtitle word ',,' too long!

Subtitle word ',,' too long!
A:   8.3 V:   2.1 A-V:  6.217 ct:  0.040   0/  0 91% 315%  8.5% 50 0 

```

Perhaps I'm just asking too much of an ION2 setup and need to start saving to replace the system with a "real" pc. Still, it would have been nice to get this to work as the box is so small that it really doesn't intrude as much as a usual PC does.

In any event, thanks for the suggestions!

---

### Post by SeijiSensei on 2012-05-12
> **ewangr said:**
> Perhaps I'm just asking too much of an ION2 setup and need to start saving to replace the system with a "real" pc.

Just avoid 10-bit H.264 encodes, and you should be fine.

---

### Post by ewangr on 2012-05-12
I think it's more than that. I have a 720p file that I KNOW isn't 10-bit, and it fails with a similar error. While another 1080p file works just fine. So it appers to be just "some" files with certain types of subs... but so far can't seem to figure out the particular issue to look out for.

---

### Post by andrew.46 on 2012-05-12
> **PolyphemusNL said:**
> I did a:

```
sudo apt-get install libsctp-dev lksctp-tools
```

...and now it compiles :)

Indeed, I have added this to the page. Although the developers are about to add in an auto check for this library....

---

### Post by andrew.46 on 2012-05-12
> **ewangr said:**
> I think it's more than that. I have a 720p file that I KNOW isn't 10-bit, and it fails with a similar error. While another 1080p file works just fine. So it appers to be just "some" files with certain types of subs... but so far can't seem to figure out the particular issue to look out for.

Is it possible you could post one of the troublesome files somewhere?

---

### Post by Eromatic on 2012-05-13
> **SeijiSensei said:**
> On the subbing group's site we have this:



**You cannot play a 10-bit encoding with VDPAU** because the H.264 decoder on the video card doesn't have support for 10-bit color.  Try playing it with the xv driver (in SMPlayer Options > Preferences > Video).  If your CPU can't keep up with a 1080p H.264 encode, then get a different version of the video.  

I just rebuilt mplayer2 from the source code at [http://www.mplayer2.org/](http://www.mplayer2.org/) the other day without incident.  You'll need to run

```
sudo apt-get install build-essential
sudo apt-get build-dep mplayer

```

to get the necessary compiler, headers and libraries.  After that it should build cleanly just by running "make" after you unpack the archive.
I believe that the tar file stuff on [http://www.mplayer2.org/](http://www.mplayer2.org/) is quite old, and probably doesn't properly support 10-bit video. You generally need to use Git Repositories - mplayer2-build.git for the most up to date version of mplayer2/libass/libav.

To install from mplayer2-build:

```
sudo apt-get install git
sudo apt-get install build-essential
sudo apt-get build-dep mplayer2  <-(If using Ubuntu 12.04 or newer)
sudo apt-get build-dep mplayer  <-(If using a version older than Ubuntu 12.04)

git clone git://git.mplayer2.org/mplayer2-build.git
cd mplayer2-build/
./init --shallow
make -j 6
```

Once the build is completed, you can then find the mplayer2 executable at /home/user/mplayer2-build/mplayer/mplayer  ...where you can point SMPlayer to. (Options / Preferences / General tab of the General Menu / mplayer executable)

To update mplayer2 of mplayer2-build:

```
cd mplayer2-build/
./clean  <-(This also deletes the mplayer2 executable.)
./update
make -j 6
```

In SMPlayer, I use gl for the video output and pulse for the audio output for best results on my nvidia card.

---

### Post by andrew.46 on 2012-05-13
I am a little curious as to why mplayer2 is preferred over MPlayer? I have read [this page]("http://www.mplayer2.org/comparison.html") but I am still a little curious :).

---

