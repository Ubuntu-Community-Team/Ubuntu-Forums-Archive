---
title: "WinFF FLV conversion. Help!"
date: 2010-03-13
forum: Multimedia Software
---

### Post by exploitations on 2010-03-13
I've been using WinFF for my website to convert videos into FLV. Well, the problem is, is that the quality comes out really bad. The audio sounds bad most of the time as well.

I tried using 
```
-vcodec flv -f flv -sameq
```

but it made the file size 3 times the size of the actual video. (And the file was FLV itself.. I wanted to see if it would work.)

I need something that will keep the quality the same, or close, and shrink the file size for faster loading on my website.

Any help would be great, thanks.

---

### Post by exploitations on 2010-03-14
anybody?

---

### Post by andrew.46 on 2010-03-14
Hi exploitations,

You might get a bit more feedback if you were interested in using FFmpeg from the commandline, perhaps tailoring your installation by following this guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Then post your full command and full terminal output here and I am pretty sure detailed help would be forthcoming.

All the best,

Andrew

---

### Post by exploitations on 2010-03-31
Just another question about WinFF, so I don't have to start a new thread.

I've been playing around with the presets, and on another post somebody said to use:

-vcodec flv -f flv -sameq

Problem is, it will only convert FLV into FLV.. which I don't see the point in that.

I tested it, and it made a 25 MB video into 260 MBs :?

I need something that will convert videos into nearly the same quality, or the same. I'm focused mainly on the audio, because I've been adding loads of music videos to my website, and the normal quality versions sound like crap.

Any help will be appreciated, thank you :)

---

### Post by FakeOutdoorsman on 2010-04-01
Can you provide some information on your input file?  The following command will suffice:
```
ffmpeg -i input.flv
```
How are you displaying these videos on your web site?  What version of Ubuntu are you using?

---

### Post by littlepeon on 2010-04-02
hey

k...dont know what ACTUAL codecs you are trying to use or what you want your final compression ratio to be...

try this

```
ffmpeg -i inputfile.xxx outputfile.flv
```

if you are trying to make a youtube like video try this:

```
ffmpeg -i mymovie.mpg -ar 22050 -acodec libmp3lame -ab 32K -r 259.97 -s 320x240 -vcodec flv mytarget.flv
```

-r is PAL or NTSC ---29.97=NTSC Pal=25
substitute the .mpg for your file codec
assumes you are using ffmpeg with libmp3lame support


does this help you?
file sizes still to big???
pleaze post

-Peon

---

### Post by exploitations on 2010-04-21
I'm using Ubuntu 9.10, and I'm using the jw player to display the videos. 

littlepeon, I tried the first code, and it made the quality pretty bad. I used the second one, and its even worse, and the file size was nearly the same size as the original.

I'm going to keep playing with it, hopefully I'll find one that works.

---

