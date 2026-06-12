---
title: "Guvcview: change format of video output"
date: 2022-02-23
forum: Multimedia Software
---

### Post by rdh61 on 2022-02-23
Guvcview saves video files as mkv by default. How do I change this to another format? Thank you.

---

### Post by Autodave on 2022-02-23
"FormatLab" is available in the snap store.  Looks like what you need.

Another way, possibly: OBS has a built in MKV to MP4 converter.

---

### Post by SeijiSensei on 2022-02-23
```
ffmpeg -i input.mkv -c copy output.mp4
```

If the Matroska file has subtitles, you need to add some additional parameters.

For a GUI solution take a look at Handbrake, but ffmpeg is the toolbox of choice for video manipulation.

---

### Post by rdh61 on 2022-02-24
> **SeijiSensei said:**
> ```
ffmpeg -i input.mkv -c copy output.mp4
```

If the Matroska file has subtitles, you need to add some additional parameters..

Thanks for that code. No subtitles. But error:

```
robert@robert-ideacentre-AIO-520-22IKU:~$ ffmpeg -i Silenced-Take1.mkv -c copy Silenced-Take1.mp4
ffmpeg version 3.4.8-0ubuntu0.2 Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.5.0-3ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version=0ubuntu0.2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Input #0, matroska,webm, from 'Silenced-Take1.mkv':
  Metadata:
    encoder         : Guvcview Muxer-2014.04
  Duration: 00:02:29.79, start: 0.000000, bitrate: 9348 kb/s
    Stream #0:0(eng): Video: msmpeg4v3, yuv420p, 640x480, SAR 1:1 DAR 4:3, 30 fps, 30 tbr, 1k tbn, 1k tbc (default)
    Stream #0:1(eng): Audio: mp3, 44100 Hz, stereo, s16p, 160 kb/s (default)
[mp4 @ 0x557633aeafa0] Could not find tag for codec msmpeg4v3 in stream #0, codec not currently supported in container
Could not write header for output file #0 (incorrect codec parameters ?): Invalid argument
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
    Last message repeated 1 times
robert@robert-ideacentre-AIO-520-22IKU:~$
```

---

### Post by ajgreeny on 2022-02-24
It looks as if mp4 is unable to contain streams using the msmpeg4v3 codec that the command asked for (the -c option is to copy both video and audio codecs) so you can either specify which codecs to use, or leave ffmpeg to use its defaults which currently i can't remember.

The conversion will take longer than if you could just copy the codecs but it should still work.

Is there a good reason for needing mp4 output files?
Any video conversions I carry out are with ffmpeg and normally to mkv which I find better than mp4.

---

### Post by ajgreeny on 2022-02-24
A web search using search-term ***msmpeg4v3 mp4 container*** quickly showed me that the **msmpeg4v3** is incompatible with mp4 containers, so I think you may either have to accept the mkv container or use ffmpeg to re-encode the video using a more common video codec such as h264 or maybe h265.

I am no expert in codecs or the pros and cons of using them, but it may be worth trying command ```
ffmpeg -i file.mkv -acodec copy -vcodec h264 outputfile.mp4
``` which I think should work for you.

---

### Post by TheFu on 2022-02-24
mkv and mp4 are "containers", not video encodings.  As ajgreeny says, looks like you'll need to transcode the video. Transcoding always - always - loses data. Whether your eyes or ears can see and hear those loses is a different question.

For converting videos between different formats, there are thousands of tools, but almost all non-commercial ones are actually ffmpeg underneath.  There are many, many, many, settings to optimize each codec based on the type of video, the required viewing platform(s), the necessary file size, and hundreds of other considerations.  Here, we will only show the minimal conversion commands and you are expected to figure out the optimal, added, settings, for your video.  Action scenes need different settings than a movie set inside a prison or anime.  

*You can make a career learning these settings.*
if you just need "good enough" video out, then I use 
 -map_metadata 0 -map 0:v -map 0:a -vcodec libx264 -crf 19 -vf scale=-1:720 -preset medium -strict experimental -c:a libvorbis -q:a 6 -qscale:a 6
in my ffmpeg commands.  I prefer mkv containers over mp4 for a number of reasons, but if you absolutely must have mp4, I think the audio cannot be vorbis, which is really too bad. Vorbis has the best quality audio of every compressed formats for the size until AAC-HQ (or whatever it is called).

I believe that besides TS containers, only mp4 support live webstreaming (we don't count flv anymore do we?). I could be wrong about this, but those are the only times I've wanted mp4.

Out of all the tools for transcoding, I've found handbrake to be both the easiest that doesn't have amputated capabilities and produces the highest quality, smallest file sizes, quicker than others - even when I've tried to have the same ffmpeg options used.

---

### Post by ajgreeny on 2022-02-24
I havent used it or seen it for years but for a small GUI application  it used to be easy to use winff, which as you might guess from its name also uses ffmpeg for the real work behind the scenes.

I'm on an Android tablet at the moment so can't look in the repos quickly to see if it's still available but I presume it is. For simple quick conversions it may be worth in investigating more fully.

---

### Post by yetimon_64 on 2022-02-25
> **ajgreeny said:**
> ...I'm on an Android tablet at the moment so can't look in the repos quickly to see if it's still available but I presume it is...
It is still available on 20.04 here...
```
apt-cache policy winff
winff:
  Installed: (none)
  Candidate: 1.5.5-6
  Version table:
     1.5.5-6 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
```
@OP, I used winff for many years up until a couple of years ago when I started using ffmpeg commands directly in the terminal and within scripting. Like ajgreeny commented I found it easy to use for quick conversions.

---

### Post by ajgreeny on 2022-02-25
I am confused by something I've just found out about guvcview and its output files; I am not getting the problem you show in post #4.

I have used it in the past but not for several years so I installed it earlier today and created a small video to test out your problem. As expected the file was an mkv but the file I created converted into an mp4 using the command suggested by SeijiSensei without a problem.
Looking at the mkv file details with **mediainfo** suggests that my mkv file is using a different video codec to yours, though my understanding of such things is perhaps a bit sketchy; it certainly is not shown as ***msmpeg4v3*** as yours was, but ***V_MPEG4/ISO/ASP*** - maybe they are the same?
```
Format                                   : MPEG-4 Visual
Format profile                           : Simple@L1
Format settings, BVOP                    : No
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (MPEG)
Codec ID                                 : V_MPEG4/ISO/ASP
Codec ID/Info                            : Advanced Simple Profile
Bit rate                                 : 17.8 Mb/s
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
```
Whether my mkv used the same codec or not, the conversion was no problem and the resultant mp4 is reported by **mediainfo** as using codec ***mp4v-20***.

I begin to wonder if we are using different libavcodec packages for our systems meaning the output mkv file is created using different codecs.  I have the following list installed.

[B][I]libavcodec-dev_4.2.4-1ubuntu0.1_amd64.deb
libavcodec-extra58_4.2.4-1ubuntu0.1_amd64.deb
libavdevice58_4.2.4-1ubuntu0.1_amd64.deb
libavfilter7_4.2.4-1ubuntu0.1_amd64.deb
ffmpeg/libavformat-dev_4.2.4-1ubuntu0.1_amd64.deb
ffmpeg/libavformat58_4.2.4-1ubuntu0.1_amd64.deb
ffmpeg/libavresample4_4.2.4-1ubuntu0.1_amd64.deb
libavutil-dev_4.2.4-1ubuntu0.1_amd64.deb
libavutil56_4.2.4-1ubuntu0.1_amd64.deb
libavcodec-extra_4.2.4-1ubuntu0.1_amd64.deb[/I][/B]

---

### Post by neu2buntu on 2022-04-12
Guvcview can also output to .webm and .avi . Click on the 'Video' tab at the top of the GUI and choose 'File' , this opens up the save location for your files. Now when the file browser window opens choose another format from the drop down menu at the bottom of this window.

---

### Post by u2nTu on 2022-04-28
> **ajgreeny said:**
> ...Is there a good reason for needing mp4 output files?...

This is the key question, thank you. Going to .mkv solves the problems with the Microsoft codec incompatibility (more screwy product from MS, expect it).

In my case, the TV rejects .avi's but will play any .mp4 (and some .mkv's). No more cheap TVs from China!

In all the Internet, this thread provided the quick, easy answer. A big thanks!

---

