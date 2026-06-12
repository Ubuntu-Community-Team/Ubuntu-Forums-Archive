---
title: "Unable to play MKVs on 14.04"
date: 2016-03-20
forum: Multimedia Software
---

### Post by cranerja on 2016-03-20
When trying to open exmaple.mkv in VLC player I am given the error message:
"No suitable decoder module: VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this."
Using Videos:
"Required plugin could not be found Videos requires to install plugins to play media files of the following type: audio/x-unknown decoder"
The video then plays without audio. The file is not corrupted and works on my other machines running 14.04. 
What could be causing this?

---

### Post by SeijiSensei on 2016-03-21
Well "undf" sounds like "undefined."  If you play the video on one of the machines where it does work, can you determine which audio codec that machine thinks is in the file?  Alternatively, install the package **mkvtoolnix** on your machine and use mkvinfo to report what audio tracks and codecs are in the file.

I use **smplayer** with **mpv** as the backend as my video player.  I install them from Doug McMahon's PPA here: [https://bugs.launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://bugs.launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by shane_faulkinbury2 on 2016-03-21
As this page says MKV files are available using VideoLAN!  [http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

Maybe uninstall and reinstall to see if that works!

---

### Post by cranerja on 2016-03-21
Hello! You are right, after posting I checked out what the audio codec was on the other machines and it is opus. I have libopus0 installed and it is still unrecognized. And as for the VLC suggestion I already am using it and the problem appears to be system wide. Thank you though!

I did have strange dependency issues when checking if libopus0 was installed; libavcodec54 was missing other dependencies. I installed everything necessary and still no dice.

---

### Post by goofprog on 2016-03-21
Just a wild guess.  Maybe VLC cannot read the format.  MKV files with opus means... it is a different format.  Usually MKV files that I see use vorbis not opus.  Try to convert the file to another format by using ffmpeg or something.  I guess the MKV files that use opus are using a VP9 codec as a guess along with opus.

---

### Post by cranerja on 2016-03-21
Hello! Thanks for the response.
I have tried using ffmpeg with this output:
```
ffmpeg version 2.8.4-1ubuntu2~ffmpegbackports1 Copyright (c) 2000-2015 the FFmpeg developers  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04)
  configuration: --prefix=/usr --extra-version='1ubuntu2~ffmpegbackports1' --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, matroska,webm, from 'Essa.mkv':
  Metadata:
    COMPATIBLE_BRANDS: iso6avc1mp41
    MAJOR_BRAND     : dash
    MINOR_VERSION   : 0
    ENCODER         : Lavf56.36.100
  Duration: 00:03:03.58, start: 0.007000, bitrate: 2656 kb/s
    Stream #0:0(und): Video: h264 (High), yuv420p(tv, bt709), 1920x1080 [SAR 1:1 DAR 16:9], 25 fps, 25 tbr, 1k tbn, 50 tbc (default)
    Metadata:
      CREATION_TIME   : 2016-01-15 09:27:00
      LANGUAGE        : und
      HANDLER_NAME    : VideoHandler
    Stream #0:1(eng): Audio: opus, 48000 Hz, stereo, fltp (default)
[mp4 @ 0x1eb3f00] Codec for stream 0 does not use global headers but container format requires global headers
[mp4 @ 0x1eb3f00] Codec for stream 1 does not use global headers but container format requires global headers
[mp4 @ 0x1eb3f00] Could not find tag for codec opus in stream #1, codec not currently supported in container
Output #0, mp4, to 'Essa.mp4':
  Metadata:
    COMPATIBLE_BRANDS: iso6avc1mp41
    MAJOR_BRAND     : dash
    MINOR_VERSION   : 0
    encoder         : Lavf56.40.101
    Stream #0:0(und): Video: h264 ([33][0][0][0] / 0x0021), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], q=2-31, 25 fps, 25 tbr, 16k tbn, 1k tbc (default)
    Metadata:
      CREATION_TIME   : 2016-01-15 09:27:00
      LANGUAGE        : und
      HANDLER_NAME    : VideoHandler
    Stream #0:1(eng): Audio: opus, 48000 Hz, stereo (default)
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): Invalid argument



```

I am taking this as there being a codec issue. ffmpeg is unable to handle it as well.

---

### Post by mc4man on 2016-03-21
> **cranerja said:**
> Hello! Thanks for the response.
I have tried using ffmpeg with this output:
.....

I am taking this as there being a codec issue. ffmpeg is unable to handle it as well.
you didn't show the ffmpeg command but you can't use opus in mp4. Either encode the audio to aac or maybe just ck. if you are using the same version of vlc on non working machine vs. working machines

Vlc here in 14.04 (2.2.1) & in 16.04 (2.2.2) both can play dash video & opus in mkv. Some earlier versions of vlc can't do dash video.
(- when dash video (AVC) is muxed into mp4 then it no longer will be 'dash' video

---

### Post by cranerja on 2016-03-21
> **mc4man said:**
> you didn't show the ffmpeg command but you can't use opus in mp4. Either encode the audio to aac or maybe just ck. if you are using the same version of vlc on non working machine vs. working machines

Vlc here in 14.04 (2.2.1) & in 16.04 (2.2.2) both can play dash video & opus in mkv. Some earlier versions of vlc can't do dash video.
(- when dash video (AVC) is muxed into mp4 then it no longer will be 'dash' video

Hello!

Yes, I know VLC can play opus in mkv. I have stated that it works on other 'identical' machines.

---

### Post by goofprog on 2016-03-22
This is what I know.  The MKV file is using the new VP9/opus combo so I also assume that opus is like DTS or AC3 so maybe a code snip like this would work....
**ffmpeg -i myfile.mkv -c:a aac -strict -2 -c:v libx264 -vf scale=-1:1080 mynewfile.mp4  **
I just place it here because it will be a viewable file after the conversion.

---

### Post by cranerja on 2016-03-22
> **goofprog said:**
> This is what I know.  The MKV file is using the new VP9/opus combo so I also assume that opus is like DTS or AC3 so maybe a code snip like this would work....
**ffmpeg -i myfile.mkv -c:a aac -strict -2 -c:v libx264 -vf scale=-1:1080 mynewfile.mp4  **
I just place it here because it will be a viewable file after the conversion.
Thank you, this does work.

But my problem is more than just one file. There is something wrong with the codecs on this machine. How do I go about fixing that?

---

### Post by goofprog on 2016-03-22
nope. everyone loves the new better HEVC format.  the problem is I cannot play it because I do not have the hardware on my laptop that is fast enough.  Maybe you just do not have all the codecs to play that file.  I would try smplayer if you have issues with a new updated version of vlc or just downgrade the files like I do and just wait for it to convert to a lower format.

---

### Post by Ambidextrous on 2016-03-22
I am having a similar issue with .mkv files, with either mpv or vlc on 15.10.  It's a new installation on an old Dell laptop.  The same files play without issue on my tablet (Andoid 4.4.2) and on my wife's laptop (a slightly newer Dell, running Windows 7, 32bit) both using vlc... and, FWIW, with every other video player available on both devices.  I don't believe for a minute that the problem is with the files.

I love vlc.  It is my video player of choice on every device that supports it.

I came back to Ubuntu after MS asked me, to allow them, to install anything on my device without further notification or permission if I accepted their "free" upgrade to Windows 10.  

UbuntuMATE worked very well on my 64bit AMD/ASUS desktop until I messed with the BIOS too much... which is why I'm using a clapped-out laptop temporarily.  A new BIOS chip is on its way from Taiwan.

My recollection (which may be flawed) is that vlc worked well, for every file type I tried, on that machine.

Nothing in the thread so far has helped, but hope springs eternally...

---

### Post by mc4man on 2016-03-22
> **Ambidextrous said:**
> I am having a similar issue with .mkv files, with either mpv or vlc on 15.10.  It's a new installation on an old Dell laptop.  The same files play without issue on my tablet (Andoid 4.4.2) and on my wife's laptop (a slightly newer Dell, running Windows 7, 32bit) both using vlc... and, FWIW, with every other video player available on both devices.  I don't believe for a minute that the problem is with the files.

I love vlc.  It is my video player of choice on every device that supports it.

I came back to Ubuntu after MS asked me, to allow them, to install anything on my device without further notification or permission if I accepted their "free" upgrade to Windows 10.  

UbuntuMATE worked very well on my 64bit AMD/ASUS desktop until I messed with the BIOS too much... which is why I'm using a clapped-out laptop temporarily.  A new BIOS chip is on its way from Taiwan.

My recollection (which may be flawed) is that vlc worked well, for every file type I tried, on that machine.

Nothing in the thread so far has helped, but hope springs eternally...
Why don't you start a new thread as your issue may be different & this thread is lacking info though not lacking mis-info 
Saying "mkv" means very little, it's a container, try to provide some info about  what's in the mkv.
ffmpeg -i your.mkv should be informative

I created a quick .mkv quite similar, (but not exact) to one posted in this thread  from a dash avc video & opus audio, I can assure you it will play back fine in both vlc, mpv or even totem in 15.10, 16.04 & last but not least  14.04
Eg.
```
ffmpeg -i '/home/doug/Desktop/see4/Rihanna - Pour It Up.mkv' 
ffmpeg version N-78590-g5590ab4 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.1)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --mandir=/usr/share/man --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab
  libavutil      55. 18.100 / 55. 18.100
  libavcodec     57. 24.103 / 57. 24.103
  libavformat    57. 25.100 / 57. 25.100
  libavdevice    57.  0.101 / 57.  0.101
  libavfilter     6. 32.100 /  6. 32.100
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  0.100 /  4.  0.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100

Input #0, matroska,webm, from '/home/doug/Desktop/see4/Rihanna - Pour It Up.mkv':
  Metadata:
    COMPATIBLE_BRANDS: [COLOR="#0000CD"]iso6avc1mp41[/COLOR]
    MAJOR_BRAND     : [COLOR="#0000CD"]dash[/COLOR]
    MINOR_VERSION   : 0
    ENCODER         : Lavf57.25.100
  Duration: 00:03:16.44, start: 0.007000, bitrate: 4092 kb/s
    Stream #0:0: Video:[COLOR="#0000CD"] h264[/COLOR] (Main), yuv420p, 1920x1080, SAR 1:1 DAR 16:9, 23.97 fps, 23.97 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      HANDLER_NAME    : VideoHandler
      DURATION        : 00:03:16.405000000
    Stream #0:1(eng): Audio: [COLOR="#0000CD"]opus[/COLOR], 48000 Hz, stereo, fltp (default)
```

Now also to mention all 3 can play a vid that constructed from vp9 & opus, notice difference in ffmpeg -i (truncated
```
see5$ ffmpeg -i '/home/doug/Desktop/see5/Rihanna - Pour It Up.mkv'
......
Input #0, matroska,webm, from '/home/doug/Desktop/see5/Rihanna - Pour It Up.mkv':
  Metadata:
    ENCODER         : Lavf57.25.100
  Duration: 00:03:16.44, start: 0.007000, bitrate: 2486 kb/s
    Stream #0:0(eng): Video: vp9 (Profile 0), yuv420p(tv, bt709/unknown/unknown), 1920x1080, SAR 1:1 DAR 16:9, 23.98 fps, 23.98 tbr, 1k tbn, 1k tbc (default)
    Metadata:
      DURATION        : 00:03:16.404000000
    Stream #0:1(eng): Audio: opus, 48000 Hz, stereo, fltp (default)

```

---

### Post by SeijiSensei on 2016-03-23
According to [this](http://news.softpedia.com/news/mplayer-based-mpv-open-source-video-player-gets-improvements-in-version-0-11-0-492583.shtml), support for Opus was added to **mpv** back in version 0.11.  The current version in Doug McMahon's [multimedia repository for Trusty]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") is 2.0.16, so give mpv a try.  (Since Doug posted right above me, he might have more to add on this subject!)

I replaced my smplayer+mplayer combination with smplayer+mpv a while back.

---

### Post by cranerja on 2016-03-23
> **mc4man said:**
> Why don't you start a new thread as your issue may be different & this thread is lacking info though not lacking mis-info 
Saying "mkv" means very little, it's a container, try to provide some info about  what's in the mkv.
ffmpeg -i your.mkv should be informative

I created a quick .mkv quite similar, (but not exact) to one posted in this thread  from a dash avc video & opus audio, I can assure you it will play back fine in both vlc, mpv or even totem in 15.10, 16.04 & last but not least  14.04
Eg.
```
ffmpeg -i '/home/doug/Desktop/see4/Rihanna - Pour It Up.mkv' 
ffmpeg version N-78590-g5590ab4 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.1)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --mandir=/usr/share/man --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab
  libavutil      55. 18.100 / 55. 18.100
  libavcodec     57. 24.103 / 57. 24.103
  libavformat    57. 25.100 / 57. 25.100
  libavdevice    57.  0.101 / 57.  0.101
  libavfilter     6. 32.100 /  6. 32.100
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  0.100 /  4.  0.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100

Input #0, matroska,webm, from '/home/doug/Desktop/see4/Rihanna - Pour It Up.mkv':
  Metadata:
    COMPATIBLE_BRANDS: [COLOR=#0000CD]iso6avc1mp41[/COLOR]
    MAJOR_BRAND     : [COLOR=#0000CD]dash[/COLOR]
    MINOR_VERSION   : 0
    ENCODER         : Lavf57.25.100
  Duration: 00:03:16.44, start: 0.007000, bitrate: 4092 kb/s
    Stream #0:0: Video:[COLOR=#0000CD] h264[/COLOR] (Main), yuv420p, 1920x1080, SAR 1:1 DAR 16:9, 23.97 fps, 23.97 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      HANDLER_NAME    : VideoHandler
      DURATION        : 00:03:16.405000000
    Stream #0:1(eng): Audio: [COLOR=#0000CD]opus[/COLOR], 48000 Hz, stereo, fltp (default)
```

Now also to mention all 3 can play a vid that constructed from vp9 & opus, notice difference in ffmpeg -i (truncated
```
see5$ ffmpeg -i '/home/doug/Desktop/see5/Rihanna - Pour It Up.mkv'
......
Input #0, matroska,webm, from '/home/doug/Desktop/see5/Rihanna - Pour It Up.mkv':
  Metadata:
    ENCODER         : Lavf57.25.100
  Duration: 00:03:16.44, start: 0.007000, bitrate: 2486 kb/s
    Stream #0:0(eng): Video: vp9 (Profile 0), yuv420p(tv, bt709/unknown/unknown), 1920x1080, SAR 1:1 DAR 16:9, 23.98 fps, 23.98 tbr, 1k tbn, 1k tbc (default)
    Metadata:
      DURATION        : 00:03:16.404000000
    Stream #0:1(eng): Audio: opus, 48000 Hz, stereo, fltp (default)

```

Okay I understand that "mkvs" work in VLC guys. As I have stated it plays on other machines I own using VLC, only with this machine not recognizing the opus audio codec. I am not looking for others to tell me that it works on their machine. Rather, I am looking for information on making the opus codec installed work.

---

### Post by cranerja on 2016-03-23
> **SeijiSensei said:**
> According to [this]("http://news.softpedia.com/news/mplayer-based-mpv-open-source-video-player-gets-improvements-in-version-0-11-0-492583.shtml"), support for Opus was added to **mpv** back in version 0.11.  The current version in Doug McMahon's [multimedia repository for Trusty]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") is 2.0.16, so give mpv a try.  (Since Doug posted right above me, he might have more to add on this subject!)

I replaced my smplayer+mplayer combination with smplayer+mpv a while back.

Thank you very much! Even though I would still like to fix the issue where Videos and VLC are both unable to recognize the opus codec, this does work. I'm very grateful!

---

### Post by mc4man on 2016-03-23
> **cranerja said:**
> Thank you very much! Even though I would still like to fix the issue where Videos and VLC are both unable to recognize the opus codec, this does work. I'm very grateful!
Make sure for Videos that gstreamer1.0-plugins-bad package is installed. Then run & post - 

```
ldd  /usr/lib/vlc/plugins/codec/libopus_plugin.so
```
```
ldd /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstopus.so

```
```
ldd  /usr/lib/vlc/plugins/codec/libavcodec_plugin.so
```
```
apt-cache policy libopus0
```

---

### Post by cranerja on 2016-03-23
> **mc4man said:**
> Make sure for Videos that gstreamer1.0-plugins-bad package is installed. Then run & post - 

```
ldd  /usr/lib/vlc/plugins/codec/libopus_plugin.so
```
```
ldd /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstopus.so

```
```
ldd  /usr/lib/vlc/plugins/codec/libavcodec_plugin.so
```
```
apt-cache policy libopus0
```

```
jacob@Murcielago:~$ ldd /usr/lib/vlc/plugins/codec/libopus_plugin.so	linux-vdso.so.1 =>  (0x00007ffcb45f0000)
	libvlccore.so.7 => /usr/lib/libvlccore.so.7 (0x00007fc6ba908000)
	libopus.so.0 => /usr/lib/x86_64-linux-gnu/libopus.so.0 (0x00007fc6ba6c0000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fc6ba2f8000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fc6ba0f0000)
	libidn.so.11 => /usr/lib/x86_64-linux-gnu/libidn.so.11 (0x00007fc6b9eb8000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fc6b9c98000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fc6b9a90000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fc6b9788000)
	libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007fc6b9540000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fc6badf8000)
```

```
jacob@Murcielago:~$ ldd /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstopus.so	linux-vdso.so.1 =>  (0x00007ffee1b68000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fc1659e0000)
	libgstaudio-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0 (0x00007fc165790000)
	libgsttag-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libgsttag-1.0.so.0 (0x00007fc165558000)
	libgstrtp-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libgstrtp-1.0.so.0 (0x00007fc165338000)
	libgstbase-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0 (0x00007fc1650e0000)
	libgstreamer-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0 (0x00007fc164dd8000)
	libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007fc164b80000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fc164878000)
	libopus.so.0 => /usr/lib/x86_64-linux-gnu/libopus.so.0 (0x00007fc164630000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fc164410000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fc164048000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007fc163dc0000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fc163ba0000)
	libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fc163998000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fc163790000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fc163588000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fc163348000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fc165ef8000)

```

```
jacob@Murcielago:~$ ldd  /usr/lib/vlc/plugins/codec/libavcodec_plugin.so	linux-vdso.so.1 =>  (0x00007ffc3b950000)
	libvlccore.so.7 => /usr/lib/libvlccore.so.7 (0x00007f81be038000)
	libavcodec.so.54 => /usr/lib/x86_64-linux-gnu/libavcodec.so.54 (0x00007f81bd2e0000)
	libavutil.so.52 => /usr/lib/x86_64-linux-gnu/libavutil.so.52 (0x00007f81bd0b8000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f81bccf0000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f81bcae8000)
	libidn.so.11 => /usr/lib/x86_64-linux-gnu/libidn.so.11 (0x00007f81bc8b0000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f81bc690000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f81bc488000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f81bc180000)
	libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f81bbf38000)
	libxvidcore.so.4 => /usr/lib/x86_64-linux-gnu/libxvidcore.so.4 (0x00007f81bbbf8000)
	libx264.so.142 => /usr/lib/x86_64-linux-gnu/libx264.so.142 (0x00007f81bb860000)
	libvpx.so.1 => /usr/lib/x86_64-linux-gnu/libvpx.so.1 (0x00007f81bb480000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f81bb1d0000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f81bafa0000)
	libtheoraenc.so.1 => /usr/lib/x86_64-linux-gnu/libtheoraenc.so.1 (0x00007f81bad60000)
	libtheoradec.so.1 => /usr/lib/x86_64-linux-gnu/libtheoradec.so.1 (0x00007f81bab40000)
	libspeex.so.1 => /usr/lib/x86_64-linux-gnu/libspeex.so.1 (0x00007f81ba920000)
	libschroedinger-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libschroedinger-1.0.so.0 (0x00007f81ba658000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f81ba438000)
	libopus.so.0 => /usr/lib/x86_64-linux-gnu/libopus.so.0 (0x00007f81ba1f0000)
	libopenjpeg.so.2 => /usr/lib/x86_64-linux-gnu/libopenjpeg.so.2 (0x00007f81b9fc8000)
	libmp3lame.so.0 => /usr/lib/x86_64-linux-gnu/libmp3lame.so.0 (0x00007f81b9d50000)
	libgsm.so.1 => /usr/lib/x86_64-linux-gnu/libgsm.so.1 (0x00007f81b9b40000)
	libfdk-aac.so.0 => /usr/lib/x86_64-linux-gnu/libfdk-aac.so.0 (0x00007f81b9890000)
	libva.so.1 => /usr/lib/x86_64-linux-gnu/libva.so.1 (0x00007f81b9678000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f81be538000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f81b9468000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007f81b91e0000)

```

```
jacob@Murcielago:~$ apt-cache policy libopus0libopus0:
  Installed: 1.1-0ubuntu1.2
  Candidate: 1.1-0ubuntu1.2
  Version table:
 *** 1.1-0ubuntu1.2 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     1.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

Thank you!

---

### Post by Petre_Cristian_Cre on 2016-03-23
You can try this .... fix ..... worked for me with vlc

[COLOR=#111111][FONT=Ubuntu]sudo apt-add-repository ppa:strukturag/libde265
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]sudo apt-get update[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt-get install vlc-plugin-libde265[/FONT][/COLOR]

---

### Post by mc4man on 2016-03-23
The lld's look ok. How about (because I see you got opus from my ppa ...that opus is the same version as in trusty just with multiarch as some users requested multiarch support
```
apt-cache policy vlc
```  

Also maybe for a file that doesn't work go vlc -vv /path/to/filename 
 The output will be large, copy all to a .txt & attach to post

---

### Post by cranerja on 2016-03-23
> **mc4man said:**
> The lld's look ok. How about (because I see you got opus from my ppa ...that opus is the same version as in trusty just with multiarch as some users requested multiarch support
```
apt-cache policy vlc
```  

Also maybe for a file that doesn't work go vlc -vv /path/to/filename 
 The output will be large, copy all to a .txt & attach to post

For the apt-cache:
```
jacob@Murcielago:~$ apt-cache policy vlcvlc:
  Installed: 2.1.6-0ubuntu14.04.1
  Candidate: 2.2.1~trusty2
  Version table:
     2.2.1~trusty2 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
 *** 2.1.6-0ubuntu14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.1.2-2build2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```
I couldn't upload the text file due to it being too large, but I noticed this:
```
[0x7fa374c01758] mkv demux error: unknown codec id=`A_OPUS'
```

---

### Post by mc4man on 2016-03-23
> **cranerja said:**
> For the apt-cache:
```
jacob@Murcielago:~$ apt-cache policy vlcvlc:
  Installed: 2.1.6-0ubuntu14.04.1
  Candidate: 2.2.1~trusty2
  Version table:
     2.2.1~trusty2 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
 *** 2.1.6-0ubuntu14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.1.2-2build2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```
I couldn't upload the text file due to it being too large, but I noticed this:
```
[0x7fa374c01758] mkv demux error: unknown codec id=`A_OPUS'
```
see here - [https://bugs.archlinux.org/task/40572](https://bugs.archlinux.org/task/40572)

So try upgrading vlc to the one from ppa -  2.2.1~trusty2
(- if you want to use the trusty media ppa fully then you should consider removing/purging that ffmpeg backports ppa first or I can point you to a companion of  the trusty-media that will be about as good as it's going to get in 14.04 media wise, ie you use Both ppa's, my other one will upgrade all those shared ffmpeg libs from the backports ppa.
If you just want to upgrade vlc to 2.2.1~trusty2 then make sure you upgrade All the vlc source packages, typically around 7

It's always best to read the ppa page fully first if you didn't before - [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by mc4man on 2016-03-23
> **SeijiSensei said:**
> According to [this](http://news.softpedia.com/news/mplayer-based-mpv-open-source-video-player-gets-improvements-in-version-0-11-0-492583.shtml), support for Opus was added to **mpv** back in version 0.11.  The current version in Doug McMahon's [multimedia repository for Trusty]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") is 2.0.16, so give mpv a try.  (Since Doug posted right above me, he might have more to add on this subject!)

I replaced my smplayer+mplayer combination with smplayer+mpv a while back.

Due to some possible issues with lts-wily I've removed release version mpv from the media ppa & there will only be 1 package going forward, available here - 
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)
It is a git master, updated weekly or more.

---

### Post by SeijiSensei on 2016-03-26
Thanks!  I've added that PPA and updated mpv.

---

