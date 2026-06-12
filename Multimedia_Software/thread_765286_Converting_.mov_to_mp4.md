---
title: "Converting .mov to mp4"
date: 2008-04-24
forum: Multimedia Software
---

### Post by s.jesudasan on 2008-04-24
hi i bought a Nokia n81 mobile and now
i want to convert the .mov files tht i have for my lappy
to mp4 or 3gp with reduced screen size
can anyone tell me how to do that

Thanks

---

### Post by moore.bryan on 2008-04-24
you could try 
```

ffmpeg -i movie.mov -f mp4 -vcodec copy -acodec copy output.mp4

```
[FONT=monospace][/FONT]

---

### Post by s.jesudasan on 2008-04-24
Sorry it didnt work

i got this message

gstalin@stalin-laptop:~/Desktop$ ffmpeg -i 0101\ -\ About\ this\ Course.mov -f mp4 -vcodec copy -acodec copy output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '0101 - About this Course.mov':
  Duration: 00:08:53.8, start: 0.000000, bitrate: 37 kb/s
  Stream #0.0(eng): Video: smc, pal8, 640x480,  5.00 fps(r)
  Stream #0.1(eng): Audio: mp2, 22050 Hz, mono
Output #0, mp4, to 'output.mp4':
  Stream #0.0: Video: smc  / 0x20636D73, pal8, 640x480, q=2-31,  5.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0xb7fb55d0]track 1: codec frame size is not set
Could not write header for output file #0 (incorrect codec parameters ?)

---

### Post by s.jesudasan on 2008-04-24
Sorry it didnt work

i got this message

gstalin@stalin-laptop:~/Desktop$ ffmpeg -i 0101\ -\ About\ this\ Course.mov -f mp4 -vcodec copy -acodec copy output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '0101 - About this Course.mov':
  Duration: 00:08:53.8, start: 0.000000, bitrate: 37 kb/s
  Stream #0.0(eng): Video: smc, pal8, 640x480,  5.00 fps(r)
  Stream #0.1(eng): Audio: mp2, 22050 Hz, mono
Output #0, mp4, to 'output.mp4':
  Stream #0.0: Video: smc  / 0x20636D73, pal8, 640x480, q=2-31,  5.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0xb7fb55d0]track 1: codec frame size is not set
Could not write header for output file #0 (incorrect codec parameters ?)

---

### Post by moore.bryan on 2008-04-24
> **s.jesudasan said:**
> gstalin@stalin-laptop:~/Desktop$ ffmpeg -i 0101\ -\ About\ this\ Course.mov -f mp4 -vcodec copy -acodec copy output.mp4
what is the "0101\ -\ About\this\"?

---

### Post by s.jesudasan on 2008-04-24
its the source file name

---

### Post by foppeh on 2009-12-17
I solved it this way:
1) Enable the medibuntu repo to get to the restricted codex: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
2) Uninstall mmpeg and install it again or make sure you run update and it gets updated.
See [https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg). The last line is most important.
3) Somehow I managed to convert to mp4, but the Android phone didn't want to play the files. I found this: [http://www.linuxquestions.org/questions/linux-mobile-81/androidg1-and-video-converted-via-ffmpeg-h263-687163/](http://www.linuxquestions.org/questions/linux-mobile-81/androidg1-and-video-converted-via-ffmpeg-h263-687163/)
It says you want particular prefixes for the Android, something like:
```
ffmpeg -i source-video.avi -s 480x320 -vcodec mpeg4 -acodec libfaac -ac 1 -ar 16000 -r 13 -ab 32000 -aspect 3:2 output-video.G1.mp4
```
My ffmpeg didn't want -aspect 3:2 and you can omit it.
4) Being GUI oriented as I am I installed WinFF. There I made a new setting with this command line:
```
-s 480x320 -vcodec mpeg4 -acodec libfaac -ac 1 -ar 16000 -r 13 -ab 32000
``` and it works! Now I can d 'n d files and automagically convert to mp4 for the Android.

Good luck

---

### Post by cen on 2010-03-06
I just got one those pocket-sized camcorders. My model is the JVC GC-FM1 and it records in MOV format files. Best converter I've used so far on Ubuntu is MobileMedia Converter. (works with FFMpeg, I believe) They even have a deb installer file for Ubuntu. Kaffeine seemed to be the only player that played the MOV file without fuss or lag, but after conversion to MP4 MPlayer plays the file without a hitch and in proper audio/video sync.

MMC can be found here:
[http://www.miksoft.net/mobileMediaConverterDown.htm](http://www.miksoft.net/mobileMediaConverterDown.htm)

Just click on the Ubuntu Linux link to grab the deb installer file.

Note that there's a PSP (playstation portable) MP4 option and an iPOD MP4 option in the software. I chose the iPOD option.

---

### Post by FiReSTaRT on 2010-04-17
WinFF is a GUI frontend for ffmpeg that did a great job for me. Apparently completely lossless conversion from MOV to AVI. It might be a dig at those of us who don't convert videos enough to know all ffmpeg parameters by heart. I'd still like to find a package that converts to Matrushka without dealing with the CLI. AFIK it has nothing to do with Windows..

---

### Post by mrhhug on 2011-01-19
FiReSTaRT , 

> I'd still like to find a package that converts to Matrushka without dealing with the CLI.


did you hear about Transmageddon? i installed it a few months back for that exact reason. i forget if its in repos or launchpad heres the site: [http://www.linuxrising.org/transmageddon/](http://www.linuxrising.org/transmageddon/)

---

### Post by lindaonline15 on 2012-02-13
hi... i tried ```
ffmpeg -i movie.mov -f mp4 -vcodec copy -acodec copy output.mp4
```
i dont get any errors but the problem is that output file does not have any sound...
any ideas whats wrong..??

---

### Post by ron999 on 2012-02-13
> **lindaonline15 said:**
>  but the problem is that output file does not have any sound...
any ideas whats wrong..??
Find out what's inside your mov file.
Use MediaInfo...
or FFmpeg like this:-
```
ffmpeg -i movie.mov
```

---

### Post by lindaonline15 on 2012-02-13
the output is some information about ffmpeg itself, followed by this:
```
Seems stream 0 codec frame rate differs from container frame rate: 25.00 (25/1) -> 3.00 (3/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '07.01.Structures.mov':
  Metadata:
    creation_time   : 2007-06-18 23:19:14
    title           : VTC Online University
    title-eng       : VTC Online University
    artist          : Virtual Training Company
    artist-eng      : Virtual Training Company
    copyright       : 1996-2005
    copyright-eng   : 1996-2005
  Duration: 00:02:17.74, start: 0.000000, bitrate: 53 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 800x600 [PAR 1:1 DAR 4:3], 20 kb/s, 3.01 fps, 3 tbr, 600 tbn, 25 tbc
    Metadata:
      creation_time   : 2007-06-18 23:19:14
    Stream #0.1(eng): Audio: mp3, 22050 Hz, 1 channels, s16
    Metadata:
      creation_time   : 2007-06-18 23:19:14
At least one output file must be specified

```

correct me if im wrong,... u wanted to see contents of my source file, not the mp4 one... right?

---

### Post by ron999 on 2012-02-13
> **lindaonline15 said:**
>  u wanted to see contents of my source file, not the mp4 one... right?
Yes, that's right.

Maybe you need to convert the "Audio: mp3, 22050 Hz, 1 channels, s16" into **aac**.
Try this command:-
```
ffmpeg -i movie.mov -f mp4 -vcodec copy -acodec aac -strict experimental output.mp4
```

---

### Post by FakeOutdoorsman on 2012-02-13
> **lindaonline15 said:**
> hi... i tried ```
ffmpeg -i movie.mov -f mp4 -vcodec copy -acodec copy output.mp4
```
i dont get any errors but the problem is that output file does not have any sound...
any ideas whats wrong..??

Can you show your actual command and the complete console output?

---

### Post by lindaonline15 on 2012-02-13
> Maybe you need to convert the "Audio: mp3, 22050 Hz, 1 channels, s16" into aac.
 Try this command:-
Code:
ffmpeg -i movie.mov -f mp4 -vcodec copy -acodec aac -strict experimental output.mp4

that works! thanks! ;)

---

### Post by lindaonline15 on 2012-02-16
Alright... so after that command worked for me, I was just trying to write a script code to automatically fetch all files, convert and rename the .mov to .mp4 as well. (this is because I have 200++ files and really dont have the time to manually convert 1 by 1)
but somehow the code does not work and I can imagine why... its because first it converts the file but still with extension .mp3 and then changes to .mp4

this is the code:
```
#!/bin/bash

for FILE in *.mov;
        do

                ffmpeg -i $FILE -f mp4 -vcodec copy -acodec aac -strict experimental $FILE
        done;


for f in *.mov;
        do
                tempfile="`basename "$f" .mov`.mp4";
                echo $tempfile;
                mv "$f" "$tempfile";
        done;
```

Anyone has a better idea to write this to solve the problem?

---

### Post by ron999 on 2012-02-16
> **lindaonline15 said:**
> 

Anyone has a better idea to write this to solve the problem?

This might do the job:-
```
for f in *.mov; do ffmpeg -i "$f" -f mp4 -vcodec copy -acodec aac -strict experimental ${f%.mov}.mp4; done
```

But it would be simple to write your own pre-set for **WinFF**.;)
Tutorial is here ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")

---

### Post by brs5tettba on 2012-04-19
I also received the message "ffmpeg codec frame size is not set".

With a little playing around, I extracted the following: "Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'"  -- my ac3 file had sample format s16.

The solution was to specify -c:a ac3 or -acodec ac3, not -c:a copy or  -acodec copy (even though the final product has the exact same format/same bitrate/same sample rate).  This let ffmpeg auto-"correct" the sample format from s16 to flt.

---

### Post by Russell Burrows on 2012-04-19
I have videos from aiptek HD camera and this is my fix:

Open shot, add .mov file , web profile, youtube hd, medium or high quality and press export and done!

That terminal stuff you folks do is very cool but I prefer simplicity of a few button presses so that my kids can watch the videos they filmed.

---

### Post by Xseba on 2012-08-07
> **foppeh said:**
> I solved it this way:
1) Enable the medibuntu repo to get to the restricted codex: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
2) Uninstall mmpeg and install it again or make sure you run update and it gets updated.
See [https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg). The last line is most important.
3) Somehow I managed to convert to mp4, but the Android phone didn't want to play the files. I found this: [http://www.linuxquestions.org/questions/linux-mobile-81/androidg1-and-video-converted-via-ffmpeg-h263-687163/](http://www.linuxquestions.org/questions/linux-mobile-81/androidg1-and-video-converted-via-ffmpeg-h263-687163/)
It says you want particular prefixes for the Android, something like:
```
ffmpeg -i source-video.avi -s 480x320 -vcodec mpeg4 -acodec libfaac -ac 1 -ar 16000 -r 13 -ab 32000 -aspect 3:2 output-video.G1.mp4
```
My ffmpeg didn't want -aspect 3:2 and you can omit it.
4) Being GUI oriented as I am I installed WinFF. There I made a new setting with this command line:
```
-s 480x320 -vcodec mpeg4 -acodec libfaac -ac 1 -ar 16000 -r 13 -ab 32000
``` and it works! Now I can d 'n d files and automagically convert to mp4 for the Android.

Good luck

gracias funciono de maravilla, a pesar de mi ingles precario, logre la conversión de mov a mp4!

---

