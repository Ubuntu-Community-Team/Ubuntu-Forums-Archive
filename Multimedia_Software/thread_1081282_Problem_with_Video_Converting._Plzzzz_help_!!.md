---
title: "Problem with Video Converting. Plzzzz help !!"
date: 2009-02-26
forum: Multimedia Software
---

### Post by paranormal on 2009-02-26
[B]Hi
I know my post mite be too long, but I have tried to share all the details of my problem that I can think of.

I have been trying to convert videos for my 6th generation Ipod. I have installed ffmpeg successfully with  x264 and Xvid ( I think so ) and have tried Thin Liquid Film and Winff for the gui interface. I am only a week old on Ubuntu as previously I was a Windows user.I use Gnome.
No matter which file i select to convert I am basically getting the same error on both the interfaces....which says File may be corrupt or may not be a valid video file. I have tried .avi, .wmv , .flv etc. but the same error.
I run both the program by giving command on the terminal and the gui opens successfully on both. 
When i run Thin Liquid Film i get the following on the terminal window.....[/B]


[COLOR="Red"]:~$ thinliquidfilm
[]
ffmpeg supports xvid
ffmpeg supports h264
tab changed
changed to "encode"
/home/punit/.thinliquidfilm/latest
1.0
Version Check:  Update message already shown
Version Check:  This is the latest version
tab changed
changed to "encode"[/COLOR]

**and the Gui Opens......but when I add the file to it I get an error whose Screen Shots I am Posting and the following adds to the output in the terminal**

[COLOR="Red"]/home/punit/Desktop/Scrubs Season 6/Scrubs.S06E11.PDTV.XviD-LOL.avi
FFmpeg version SVN-r17543, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.18. 0 / 52.18. 0
  libavformat   52.29. 2 / 52.29. 2
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb 23 2009 22:12:26, gcc: 4.3.2
/home/punit/Desktop/Scrubs Season 6/Scrubs.S06E11.PDTV.XviD-LOL.avi: Unknown format
Values:
parsing error
[/COLOR]

[B]When I run Winff in the same way, when I try to convert the terminal gives me the following error code...
[/B]

[COLOR="Red"]\033]0; Converting Scrubs.S06E12.PDTV.XviD-NoTV.avi (1/1)\007FFmpeg version SVN-r17543, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.18. 0 / 52.18. 0
  libavformat   52.29. 2 / 52.29. 2
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb 23 2009 22:12:26, gcc: 4.3.2
[NULL @ 0x9671600]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997003/125000)
Input #0, avi, from '/home/punit/Desktop/Scrubs Season 6/Scrubs.S06E12.PDTV.XviD-NoTV.avi':
  Duration: 00:20:58.88, start: 0.000000, bitrate: 1162 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 512x384 [PAR 1:1 DAR 4:3], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
/usr/local/bin/ffmpeg: unrecognized option '-me'
Press Enter to Continue[/COLOR]


[B]This is the only problem I have come across so far and I am sure u guys would be having a solution.

PLZ PLZ Help me. :([/B]

---

### Post by wolfen69 on 2009-02-26
try [Handbrake]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb") for ipod formats. it takes 2 clicks to convert. easiest solution i've found. just click the .deb file to install it.

when you open handbrake, to the right, you will see "presets". change it to "ipod", and you are good to go.

this is assuming you are using ubuntu 8.10

---

### Post by paranormal on 2009-02-27
Thanks wolfen69..:)

I tried HandBrake ,it works and pretty much simple to use :):). Though I found it to be slow as compared to the alternatives I've used previously (on Windows).

But still if possible I am keen on knowing a solution to my problem. Why both Thin Liquid Film and Winff dont work ?? 	:confused:

Thanks for the quick reply....

---

### Post by FakeOutdoorsman on 2009-02-27
You're using a more recent revision of FFmpeg than what thinliquidfilm is used to, but it can be fixed: [Strange ThinLiquidFilm Issue](http://ubuntuforums.org/showthread.php?t=785003).

You need new presets for WinFF.  The default presets are too old to use with svn FFmpeg.  A fix is described here: [WinFF not working with ffmpeg?](http://ubuntuforums.org/showpost.php?p=6609161&postcount=8)

You can also skip these GUIs and use FFmpeg directly.  Since you already have a recent enough FFmpeg, you can use the libx264 presets and probably get a better quality than what the GUIs will provide:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -vpre ipod640 -crf 28 -threads 0 output.mp4
```
Adjust the CRF value as necessary.  A higher number is lower quality, but a smaller file size and generally a faster encode.  I usually use 24-30, but that is personal preference.  If you use the ipod640 preset (there is also an ipod320 preset) you will then need to run the file through AtomicParsley:
```
AtomicParsley butterfly-ipod.mp4 --DeepScan --iPod-uuid 1200 --overWrite --artist "AlaskaRobotics.com" --title "Butterfly Kisses" --description "Watching butterflies flutter by" --copyright "©2009 Alaska Robotics"
```

---

### Post by paranormal on 2009-03-01
Thanks for the quick response and the solution  FakeOutdoorsman :) . Finally got Thin Liquid Film working......:)

Also thanks for the command line use. Its really nice and fast :D. Does it support Queuing ?...:confused:

Also I am unable to mark this Thread as solved......I read it somewhere that the function is disabled....:(

Thanks for YOUR HELP and support....:)

---

