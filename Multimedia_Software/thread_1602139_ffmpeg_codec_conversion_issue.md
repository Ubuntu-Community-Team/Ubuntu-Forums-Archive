---
title: "ffmpeg codec conversion issue"
date: 2010-10-21
forum: Multimedia Software
---

### Post by MikeyDL on 2010-10-21
I'm on Ubuntu 10.10 x64.

Trying to convert MOD files using ffmpeg.  Been researching quite a bit and stumbled upon this command to convert:

```
ffmpeg -i <inputfile>.MOD -deinterlace -vcodec h264 -b 4000k -acodec aac -ab 192k <output>.mov
```

However, when running the command I get the error message: unknown encoder h264.  

I've also downloaded a script mod2avi but when I run that get an similar error message:  unkown encoder xvid.

I've tried adding lib (suggested in forum posts) to the h264 and xvid.  I"ve installed restricted-extra and tried figuring it out from a 96 page post on the subject but hard to get a sense of what I need to do to get these vid codecs working for ffmpeg.

Anyone have an idea on how to get those codecs working for 10.10 ffmpeg?

Thanks!

---

### Post by andrew.46 on 2010-10-21
Hi MikeyDL,

Unfortunately the repository FFmpeg has been stripped of several important codecs including the ones responsible for encoding to aac and h264. For Maverick you can try adding the Medibuntu repository:

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```

and then add the required libavcodec package:

```

sudo apt-get install ffmpeg libavcodec-extra-52

```

The syntax of your commandline is a little off, *-acodec libfaac* should work rather than *-acodec aac* which will ask for the native encoder. Is there a special reason for mov container?

All the best,

Andrew

---

### Post by MikeyDL on 2010-10-21
Hi and thanks for the information!

I couldn't remember what it was called but I had installed libavcodec-extra-52.  I just couldn't remember what it was called when I wrote my post.  

Even with that I still get error messages for mod2avi script and ffmpeg converts:

mod2avi:

[color=blue]d --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg @ 0xcb8640]max_analyze_duration reached
Input #0, mpeg, from 'MOV001.MOD':
  Duration: 00:00:57.02, start: 0.220756, bitrate: 5093 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9600 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
Unknown encoder 'xvid'
[] Done converting MOV001.MOD!
[] Number of files converted: 1
[/color]

For ffmpeg:

[color=blue]
[mpeg @ 0x1483640]max_analyze_duration reached
Input #0, mpeg, from 'MOV001.MOD':
  Duration: 00:00:57.02, start: 0.220756, bitrate: 5093 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9600 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
Unknown encoder 'h264'
[/color]

It's not a huge deal.  I can still convert with pitivi and open shot but liked the control with ffmpeg so curious on what the deal was.

The container choice was just because that was the specific code I got from one of the post talking about the issue.  No container preference, I usually prefer avi or mkv (subtitles).

Thanks!

---

### Post by andrew.46 on 2010-10-21
Hi mikey,

I have had a look at mod2avi and I suspect all you need to do is modify a few variables to get it to work. Specifically lines 10 and 11:

```

fileext='avi'            # File extension to use for converted files (avi, mp4, flv, etc)
vcodec='xvid'            # Default value: video codec (xvid, mpeg4, flv, etc)

```

Perhaps you could try *fileext='mp4'* and *vcodec='**[COLOR="Red"]lib[/COLOR]**xvid'* and this would get the script kick-started for you? As you can see there has been a codec name change from xvid to libxvid, as for the avi container that is just very old technology :). There is some room for experimentation with this script.

For your straight FFmpeg conversion you will need to show the commandline that you have used and the full terminal output but I suspect you have misnamed the encoder, it should be *-vcodec libx264*. There are some presets available to use here although I am not sure exactly which ones are available for the repository FFmpeg, I use a different version :(. But perhaps the following will work for your file, I can see the slow preset on the Maverick filelist:

```

ffmpeg -i MOV001.MOD -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 MOV001.mp4

```

Thanks to FakeOutdoorsman for this syntax :)

Andrew

---

### Post by MikeyDL on 2010-10-21
Thanks Andrew!

That made some progress.  For the ffmpeg output I'm getting an unknown encoder for libfaac.  The full output of the conversion is:

[http://pastebin.com/1XdiHcC1]("http://pastebin.com/1XdiHcC1")

Perhaps if I used a different audio codec?

Is there an ffmpeg command to list installed video, container and audio codecs?

---

### Post by andrew.46 on 2010-10-21
Hi Mikey,

> **MikeyDL said:**
> Perhaps if I used a different audio codec?

Indeed, although the absence of libfaac is a little puzzling. mp3 encoding:

```

ffmpeg -i MOV001.MOD -acodec libmp3lame -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 MOV001.mp4

```

> Is there an ffmpeg command to list installed video, container and audio codecs?

It varies from version to version but the repository version should respond to *ffmpeg -formats*, newer versions have *ffmpeg -codecs*, *ffmpeg -filters* and a few others...

Andrew

---

### Post by MikeyDL on 2010-10-21
Changing the audio codec did the trick.  The original MOD file was 10MB and the output file was 9.8MB so a nice sized output result.

I do have the repository ffmpeg installed (I guess) since the ffmpeg -format outputed a list.

[http://pastebin.com/70CcVPQL]("http://pastebin.com/70CcVPQL")

both aac and h264 were on the list but perhaps the actual variable name to reference is different.  

Regardless at least I have some of the basics working!

---

### Post by andrew.46 on 2010-10-21
Hi Mike,

I have just followed my own advice and installed FFmpeg and libavcodec-extra-52 onto my Maverick VM and sure enough aac encoding is not possible through libfaac, only through *-acodec aac* which is not the best way to go...

Looks like a naming problem between Maverick Repository and Medibuntu and I am not sure the easiest way to get around this. If you search Synaptic for libavcodec-extra-52 you will see 2 versions, one marked 4:0.6-2ubuntu3 (maverick) and another marked 4:0.6-2ubuntu+medibuntu1(packages.medibuntu.org). You need to 'Force' the medibuntu version and then you will have aac encoding through libfaac:

```

andrew@ilium:~/Desktop$ **[COLOR="Red"]ffmpeg -codecs | grep aac[/COLOR]**
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
 DEA    aac             Advanced Audio Coding
**[COLOR="Red"]  EA    libfaac         libfaac AAC (Advanced Audio Codec)[/COLOR]**

```

I am a little surprised that this has not been noticed before, admittedly I compile the svn and this is the first time I have looked closely at the Medibuntu libavcodec...

Andrew

---

