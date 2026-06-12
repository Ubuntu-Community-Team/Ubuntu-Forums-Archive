---
title: "Converting flv. to mp4"
date: 2008-06-24
forum: Multimedia Software
---

### Post by ffmpegfailure on 2008-06-24
Sorry if this had already been posted, im new to the forums. I'm trying to convert flv. files to mp4, or other iPOD compatible formats. I've had a play with ffmpeg after looking at some other threads but so far no luck. Any help, the simpler the possible as I have a very limited understanding of ubuntu would be greatly appreciated.

---

### Post by cozmicharlie on 2008-06-24
try avidemux - it is in Synaptic.  Should work for you.

---

### Post by rainwalker on 2008-06-24
If you have ffmpeg, google WinFF. It's a nice GUI for ffmpeg that makes converting formats simple

---

### Post by ffmpegfailure on 2008-07-04
Still no luck. I installed WinFF and it looked like it was all going to work, until I got told it could not find/did not recognise the codecs (in particular aac and xvid?). I don't know if I've installed a dud version of ffmpeg or what. All help appreciated.

---

### Post by gandaran on 2008-07-04
> **ffmpegfailure said:**
> Still no luck. I installed WinFF and it looked like it was all going to work, until I got told it could not find/did not recognise the codecs (in particular aac and xvid?). I don't know if I've installed a dud version of ffmpeg or what. All help appreciated.

you need to install ffmpeg from the medibuntu repository, not the regular ubuntu repository's.

---

### Post by rainwalker on 2008-07-04
> **gandaran said:**
> you need to install ffmpeg from the medibuntu repository, not the regular ubuntu repository's.

+1 for that

---

### Post by ubuntu-freak on 2008-07-04
First of all, execute this command in the terminal:
 
**sudo apt-get purge ffmpeg**
 
Then complete at least part 1 and 3 of my [how-to](ubuntuforums.org/showthread.php?t=766683).

---

### Post by ffmpegfailure on 2008-07-06
Thought I'd finally got it. The command 
```
:~$ sudo apt-get purge ffmpeg
E: Invalid operation purge

```
just leaves me with this. Maybe I'll try installing it from medibuntu repository. Where/what is this?

---

### Post by soxs on 2008-07-06
try ```
sudo apt-get remove --purge ffmpeg
``` though ```
apt-get purge 
```works for me aswell

---

### Post by rainwalker on 2008-07-06
The medibuntu repos are the repos for multimedia and video codecs that can't be included in Ubuntu by default. Here: [http://www.medibuntu.org/](http://www.medibuntu.org/)

Also, check this out for everything else multimedia-related: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by SPARTAN-118 on 2009-07-04
Don't close this thread yet! 

My video(s) I'm trying to convert is/are .flv (Flash) files dragged from the /tmp directory. They're from Youtube. I'm trying to convert it/them to an iPod video format.

My WinFF doesn't give an error about FFmpeg; it just says "home/matthew/Videos/[filename]: No such file or directory
Press Enter to continue

Well, I know for certain my video exists (I can play it), so why can't FFmpeg convert it?
Oh, and avidemux, it displays this message:
Save (A+V) will generate bad AVI. Save audio will work.

Well, first of all, I don't want an AVI file; I want a .mp4 or .mov file (iPod).
Second: I don't see a "Save Audio" button, and I want the video, too! And when I try to play/preview the file (in Avidemux) it's just a green box.

REALLY, HOW HARD IS IT TO GET VIDEOS ON YOUR iPod IN LINUX?!
I'd be better off just copying my files to Windows, and converting them there and putting them on my iPod via iTunes.

Why isn't iTunes available for Linux yet? They'd get even more customers if they made their easy-to-use software available to more people (though the fact that iTunes *copies* all your files - essentially taking up more room - might be a downer, it sure is easier than importing a bunch of stuff and adding it to the iPod, then learning you can't delete it, like in Rythmbox, or having to compile a bunch of source code to build a program that doesn't even convert your file).

---

### Post by sdlynx on 2009-07-04
Hmm first of all you should know that you can download videos from youtube in mp4 format.  The flv videos are the low quality and the mp4 videos are the high quality versions of these videos.

Regardless, there is an online converter ([http://media-convert.com](http://media-convert.com)) that will convert your flv files to mp4 without trouble.  If they're youtube videos they shouldn't be too big to upload.

> **SPARTAN-118 said:**
> 
Why isn't iTunes available for Linux yet? They'd get even more customers if they made their easy-to-use software available to more people (though the fact that iTunes *copies* all your files - essentially taking up more room - might be a downer, it sure is easier than importing a bunch of stuff and adding it to the iPod, then learning you can't delete it, like in Rythmbox, or having to compile a bunch of source code to build a program that doesn't even convert your file).
You can delete files by right clicking the song/video you want to remove and clicking move to trash or something of that sort.  You can also use gtkpod to sync up with your iPod.  Lastly, you can set iTunes so that it does not copy all of the music you add to the library, instead it just reads the music from where you added it (you can change this from the Preferences or something).

---

### Post by paul.gevers on 2009-07-05
> **SPARTAN-118 said:**
> My WinFF doesn't give an error about FFmpeg; it just says "home/matthew/Videos/[filename]: No such file or directory
Press Enter to continue

Are there any special characters in your filename? If I am correct WinFF does not (yet) check properly to escape command line characters. So it might help to rename the file to something obviously correct.

---

### Post by foxoman on 2009-07-05
[COLOR=Black]You Can use Mobile Media Converter , it come with its own ffmpeg , so you don not need to install any thing .

***Download*** :  [**[SIZE=2] [/SIZE]**]("file:///media/data/mic/MIKSOFTreloaded/mobileMediaConverterDown.htm")[[SIZE=-1]**Ubuntu Linux,**[/SIZE][SIZE=-1]** mmc_1.4.3_i386.deb, **[/SIZE]]("http://www.miksoft.net/products/mmc_1.4.3_i386.deb")[SIZE=-1]**[ 4.4 MB]("http://www.miksoft.net/products/mmc_1.4.3_i386.deb") **[/SIZE][/COLOR]

---

### Post by SPARTAN-118 on 2009-07-09
> **sdlynx said:**
> Hmm first of all you should know that you can download videos from youtube in mp4 format.  The flv videos are the low quality and the mp4 videos are the high quality versions of these videos.

Regardless, there is an online converter ([http://media-convert.com](http://media-convert.com)) that will convert your flv files to mp4 without trouble.  If they're youtube videos they shouldn't be too big to upload.


You can delete files by right clicking the song/video you want to remove and clicking move to trash or something of that sort.  You can also use gtkpod to sync up with your iPod.  Lastly, you can set iTunes so that it does not copy all of the music you add to the library, instead it just reads the music from where you added it (you can change this from the Preferences or something).

Heh heh heh... GTKpod for some reason is crap with my iPod, but Hipo iPod Manager works fine, though both are a hassle compared to iTunes...

Also, my iPod is a (3rd Generation?) iPod Nano, as in, the first Nano that plays videos, not the Chromatic. (Next iPod I get will be the Touch, so obviously I can't use it with Linux, though Hipo displays it in the Preferences -> Model # drop-down box).

SPARTAN-118

---

### Post by HappyFeet on 2009-07-10
Has no one heard of [Handbrake]("http://handbrake.fr/?article=download")? One click to convert videos to mp4. Enjoy.

---

### Post by rainwalker on 2009-07-10
> **HappyFeet said:**
> Has no one heard of [Handbrake]("http://handbrake.fr/?article=download")? One click to convert videos to mp4. Enjoy.

I was not aware HandBrake could convert videos, I thought it was just for ripping DVDs. Good tip :)

---

### Post by SPARTAN-118 on 2009-07-10
Thank you paul.gevers, WinFF is stupid that way:
When trying to convert videos, it cannot do so with a - . , : " ; [] () in the filename.
So, basically, if your filenames are only alphanumeric, the conversion *should* work;
if you have even one dash, the conversion will fail and you will get the same error as i did.

SPARTAN-118

---

### Post by paul.gevers on 2009-07-12
> **SPARTAN-118 said:**
> Thank you paul.gevers, WinFF is stupid that way:
When trying to convert videos, it cannot do so with a - . , : " ; [] () in the filename.
So, basically, if your filenames are only alphanumeric, the conversion *should* work;
if you have even one dash, the conversion will fail and you will get the same error as i did.

SPARTAN-118

Thank you for reporting. I already had a bug open for this issue (although I thought it was only the " that was the problem....)

See [winff bug 38]("http://http://code.google.com/p/winff/issues/detail?id=38")

---

### Post by SuperSonic4 on 2009-07-12
You could always read the man page for command-line ffmpeg and go from there (A). It'd probably be easier to download the videos from youtube using downloadhelper or something similar though

---

### Post by FakeOutdoorsman on 2009-07-12
FFmpeg can create high quality iPod compatible h.264 videos.  Intrepid (and newer) users will only need to enable restricted encoders in FFmpeg:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

Everyone else will need to compile FFmpeg first because FFmpeg from the repository is too old and doesn't include the new presets:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Now the command:
```
ffmpeg -y -i input.avi -pass 1 -vcodec libx264 -vpre fastfirstpass -vpre ipod640 -b 512k -bt 512k -s 640x480 -threads 0 -f ipod -an /dev/null && ffmpeg -i input.avi -pass 2 -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -vpre ipod640 -b 512k -bt 512k -s 640x480 -threads 0 -f ipod output.mp4
```
It's a long command, but that's because it is a two-pass encode.  Adjust these options as you see fit:
[indent]**input.avi**: example input file name
**output.mp4**: example output file name
**-s**: video frame size
**-ab**: audio bitrate
**-b** and **-bt**: bitrate[/indent]
You may have to run the output from FFmpeg through MP4Box (part of the **gpac** packge in the repository) if you want it to work with iTunes.  It has been a while since I've tested this though since I do not own an iPod or use iTunes:
```
MP4Box -add ffmpegoutput.mp4 finaloutput.mp4
```

---

### Post by zhongguohua88 on 2010-05-09
I have managed to convert videos with Avidemus but it only converts them one at a time and I have to convert a lot. I have tried using WinnFF many times and I always get this error message:
> FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004BE337D8B86A003C1E42D09CDA3A-2590-6A29-3682-E76DF63B08E9.flv':
  Duration: 00:03:31.40, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x264 [PAR 11:12 DAR 11:9], 192 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004B0B7890EE53003C1E42995EA5C8-593F-D600-0DEA-6E426E59AD43.flv':
  Duration: 00:04:57.26, start: 0.000000, bitrate: 171 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], 171 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004BE321F22B08003C1E4259E25290-49D2-3278-6E9F-B8FB938FDB81.flv':
  Duration: 00:06:55.00, start: 0.000000, bitrate: 171 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x264 [PAR 11:12 DAR 11:9], 171 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004BE32185C3EA003C1E429D1369A0-03D1-1912-D4E1-876DD8A501C5.flv':
  Duration: 00:04:15.33, start: 0.000000, bitrate: 175 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x264 [PAR 11:12 DAR 11:9], 175 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004BE3207EB698003C1E4225134BEB-7FEE-CA8C-0E83-4EF37704BE4F.flv':
  Duration: 00:05:58.66, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x264 [PAR 11:12 DAR 11:9], 192 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004BE31E37CEBD003C1E42DDC56071-AE8A-E198-CE89-154B4351941C.flv':
  Duration: 00:06:03.60, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x264 [PAR 11:12 DAR 11:9], 192 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004BE31E5ADA6D003C1E42413B259C-04BA-F66A-67B6-DFD898C7A9DA.flv':
  Duration: 00:04:44.13, start: 0.000000, bitrate: 193 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x264 [PAR 11:12 DAR 11:9], 193 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004BE3383DC0C4003C1E42CC6F7CEA-6141-B598-056D-E0B2E25D772E.flv':
  Duration: 00:05:11.00, start: 0.000000, bitrate: 188 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x264 [PAR 11:12 DAR 11:9], 188 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004B06BF8988D6003C1E42AE191115-47A6-A406-F612-6C43F345B5F0.flv':
  Duration: 00:04:26.33, start: 0.000000, bitrate: 171 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], 171 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004B314496598C003C1E42E83275E9-E111-64DE-47EA-33F6EDEB50D9.flv':
  Duration: 00:04:25.06, start: 0.000000, bitrate: 179 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], 179 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004B0B78579A70003C1E42ECBE6C2A-FD59-298D-EFCC-2D67F76E927C.flv':
  Duration: 00:04:01.06, start: 0.000000, bitrate: 171 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], 171 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004B3917775AA4003C1E42BB0E3CAF-01EB-2040-9984-3D8BD9241530.flv':
  Duration: 00:03:56.93, start: 0.000000, bitrate: 177 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], 177 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, flv, from '/media/446C7A0C6C79F94E/Users/Tsui Zi Hin/Desktop/Downloads/03000201004B450D5D3E4A003C1E4238FD2AFB-AF3B-4957-EF8D-4C4DBCBAB953.flv':
  Duration: 00:03:49.53, start: 0.000000, bitrate: 194 kb/s
    Stream #0.0: Video: h264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], 194 kb/s, 15 tbr, 1k tbn, 30 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libx264'
Press Enter to Continue


---

### Post by seventeener on 2011-07-05
The following works for me:
VLC media player -> Media -> Convert/Save.

---

