---
title: "Can't use WinFF to convert MPEG to iPod/H.264"
date: 2010-11-09
forum: Multimedia Software
---

### Post by jdholman on 2010-11-09
Hello:

I am running 10.10 64-bit and am trying to get an option in WinFF to convert an MPEG file to an iPod compatible video.  All of the HOT_TO guides I could find involve installing the FFmpeg libraries, which I have done as well as I could have.

The problem is that within WinFF, I don't see anything different in the "Convert To ..." drop-down.  The Wiki I am reading tells me to select iPod, but this isn't available.

What do I need to do to get this to be selectable?

Thanks,

Jim

---

### Post by ron999 on 2010-11-09
Hi
Are you sure you haven't got an option Convert To...  iPod-iTunes ?

---

### Post by jdholman on 2010-11-09
Maybe I am missing something here.  It looks like the "Convert To ..." needs to be "Rockbox".

When I select Rockbox and then select "RB Apple iPod Video Widescreen", I can convert the video, but the output file is another MPG and not an M4V file.

What should I be doing in WinFF to create an M4V output file?

Thanks,

Jim

---

### Post by jdholman on 2010-11-09
Ron,

I wish I had that choice.  Here is a screenshot of my WinFF "Convert To ..."

Jim

---

### Post by ron999 on 2010-11-09
OK Jim
I think that you need to update your presets file.

The instructions are here:-[http://code.google.com/p/winff/wiki/InstallPresetsxml]("http://code.google.com/p/winff/wiki/InstallPresetsxml")

In my case, I'm the only user so I can do this:-
> If you just want to install for the current user, unzip/untar the downloaded file and copy the new presets.xml file to /home/user/.winff/ 

It looks like there are two versions available.
One for libavcodec51 and one for libavcodec52.
To find out which libavcodec you have, enter **ffmpeg** in the terminal.

---

### Post by jdholman on 2010-11-09
Ron,

Maybe this is closer.  I'm not sure...

I pulled the new DEB package for WinFF and got the new Presets file for Libavcodec52 and tried again to convert the MPEG to iPod Widescreen.

Here is the output I received.
The big errors are:

invalid dts/pts combination
broken ffmpeg default settings detected
use an encoding preset (vpre)
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

What do you think?

Jim

  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg @ 0x8dd640]invalid dts/pts combination
    Last message repeated 120 times
Input #0, mpeg, from '/home/jim/Videos/MOV04929.MPG':
  Duration: 00:00:30.86, start: 0.070000, bitrate: 10492 kb/s
    Stream #0.0[0x1c0]: Audio: mp2, 32000 Hz, 1 channels, s16, 64 kb/s
    Stream #0.1[0x1e0]: Video: mpeg1video, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 104857 kb/s, 30 fps, 30 tbr, 90k tbn, 30 tbc
[libx264 @ 0x8e0970]broken ffmpeg default settings detected
[libx264 @ 0x8e0970]use an encoding preset (vpre)
Output #0, ipod, to '/home/jim/MOV04929.m4v':
    Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, 2 channels, s16, 112 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
Press Enter to Continue

---

### Post by ron999 on 2010-11-09
Hi
I have the same error report as you when using iphone widescreen.

> [buffer @ 0x9e8df30] w:504 h:284 pixfmt:yuv420p
[scale @ 0x9ea1780] w:504 h:284 fmt:yuv420p -> w:480 h:320 fmt:yuv420p flags:0xa0000004
[libx264 @ 0x9e91350] broken ffmpeg default settings detected
[libx264 @ 0x9e91350] use an encoding preset (vpre)
Output #0, ipod, to '/home/ron/WinFF_output/Serpico.m4v':
    Stream #0.0(und): Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1(und): Audio: libfaac, 48000 Hz, 2 channels, s16, 112 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


I think it's because the supplied winff presets file is out of date.
I know that the error 
[COLOR="Red"][libx264 @ 0x8e0970]use an encoding preset (vpre)[/COLOR]
is because the latest versions of x264 need to use a **vpre** preset.
 
The winff preset file uses parameters instead of a vpre preset.
Like this:-
> -r 29.97 -vcodec libx264 [COLOR="Red"]-flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -crf 21 -bt 256k -refs 1 -coder 0 -me_method full -me_range 16 -subq 5 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -s 480x320 -aspect 16:9[/COLOR] -acodec libfaac -ab 112k -ar 48000 -ac 2

I don't know how to get around this.:confused:

---

### Post by jdholman on 2010-11-09
Ron,

I ended up uninstalling WinFF and GStreamer from the Software Center and reinstalling them both.

I now have a slightly different presets.xml file with a choice for Google Android which is actually my phone.  Would you believe it works now?  Go figure.

Jim

---

### Post by gordintoronto on 2010-11-09
> **jdholman said:**
> Hello:

I am running 10.10 64-bit and am trying to get an option in WinFF to convert an MPEG file to an iPod compatible video.  All of the HOT_TO guides I could find involve installing the FFmpeg libraries, which I have done as well as I could have.


Perhaps you could explain exactly what you did?

---

### Post by Wizard.Semfe on 2010-12-03
The answer seems to be adding the option "-vpre hq".

Found it here:
[http://code.google.com/p/winff/issues/detail?id=90#c0](http://code.google.com/p/winff/issues/detail?id=90#c0)


Edit: Now the video is not playable by iphone though :(

---

### Post by FakeOutdoorsman on 2010-12-03
Forget WinFF.  The H.264 iPod presets are terribly out of date (otherwise you can make your own presets if you want to use WinFF). Try using FFmpeg directly:

1. Enable additional encoders.  FFmpeg from the repository doesn't have all of the required encoders enabled. There are several options:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

With the above link: if you want the latest and greatest and are not adverse to some easy compiling then follow option A.  If you want the "easiest" option, then try option C.

2. The command:
```
ffmpeg -i input.ogv -vcodec libx264 -vpre medium -vpre ipod640 -crf 26 -map_meta_data 0:0 \
-s 640x480 -acodec libfaac -aq 100 -threads 0 output.mp4
```

This should work with a compiled FFmpeg from SVN (option A above) or FFmpeg from the Ubuntu Maverick Meerkat 10.10 repository.  If it doesn't work, then try adding **-f ipod** (I don't own any of these Apple devices, so I can't test to make sure).

Those of you that compiled FFmpeg can replace **-s 640x480** with **-vf scale=640:-1** which will allow FFmpeg to automatically determine the correct height while keeping the aspect correct. It won't work if the output is an odd size, but FFmpeg will tell you and you can just provide a manual value (such as **-vf scale=640:360**).

---

### Post by Wizard.Semfe on 2010-12-06
Managed to make a playable file for iphone using the following:
ffmpeg -i input.mp4 -vcodec mpeg4 -map_meta_data 0:0 -s 480x320 -acodec libfaac output.m4v
Thanks FakeOutdoorsman for the help.

---

### Post by andrew.46 on 2010-12-07
Hi Wizard,

> **Wizard.Semfe said:**
> Managed to make a playable file for iphone using the following:
```
ffmpeg -i input.mp4 -vcodec mpeg4 -map_meta_data 0:0 -s 480x320 -acodec libfaac output.m4v
```
Thanks FakeOutdoorsman for the help.

Good to hear success :). You might find even better results using x264 for the video encoding rather than mpeg4 though. If however you are more than happy with mpeg4 you might consider adding in quality or bitrate settings for the video (and the audio), as it is you are currently accepting the FFmpeg *defaults*...

Andrew

---

