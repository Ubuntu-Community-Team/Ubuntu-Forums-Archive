---
title: "conversion"
date: 2009-09-01
forum: Multimedia Software
---

### Post by blackmail on 2009-09-01
what i would really want to know is why are there no good conversion programs (could be that there are just that i don't know of any...), ffmpeg is the one i know about, but either i am stupid, or that program really is rocket science...
Could any one tell me how to exactly use it, and if there are some windows style converters...?
thank you

---

### Post by blackmail on 2009-09-01
why do answers come so hardly?

---

### Post by Malta paul on 2009-09-01
Hi,
I use Gnome sound converter (for audio)
Applications>Add/Remove Search for Sound converter.

:D

---

### Post by FakeOutdoorsman on 2009-09-01
> **blackmail said:**
> Could any one tell me how to exactly use it...
FFmpeg is an excellent audio and video converter, but this is a very vague and general request.  What do you want to do exactly?

Three good starting points:
[list][*] [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)
[*] [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/)
[*] [Using ffmpeg to manipulate audio and video files](http://howto-pages.org/ffmpeg/)[/list]

> and if there are some windows style converters...?
[WinFF](http://winff.org) is worth trying.  You could also try [Sinthgunt](http://code.google.com/p/sinthgunt/).  I don't have any experience with these.

---

### Post by blackmail on 2009-09-01
well first of all i would like to convert from flv files to avi or mp4 files, and of course audio conversions such as from flac files to mp3...but i will read the aticles you posted and i will give a feedback as to what i did or did not understand

---

### Post by Revolutionary101 on 2009-09-01
WinFF and Avidemux are good converters. WinFF is very simple and easy to use and Avidemux is harder to use but offers many options. For audio conversions I suggest using soundKonverter.

---

### Post by Catarina on 2009-09-01
> **blackmail said:**
> what i would really want to know is why are there no good conversion programs (could be that there are just that i don't know of any...), ffmpeg is the one i know about, but either i am stupid, or that program really is rocket science...
Could any one tell me how to exactly use it, and if there are some windows style converters...?
thank you
  
Well, for a good video transcoder, you've got [Handbrake]("http://handbrake.fr/"). It's open source, GPL-licensed, multiplatform and multithreaded.

[CENTER][IMG]http://trac.handbrake.fr/raw-attachment/wiki/LinGuiScreenshots/HandBrake-Pic.jpeg[/IMG]

[quote=http://handbrake.fr/?article=details]


**Supported sources:**
 
[LIST]
[*]Any DVD-like source: VIDEO_TS folder, DVD image or real DVD (unencrypted--protection methods including CSS are not supported internally and must be handled externally with third-party software and libraries), and some .VOB and .TS files
[*]Most any multimedia file it can get libavformat to read and libavcodec to decode.
[/LIST]
 
**Outputs:**
 
[LIST]
[*]File format: MP4, MKV, AVI or OGM
[*]Video: MPEG-4, H.264, or Theora (1 or 2 passes or constant quantizer/rate encoding)
[*]Audio: AAC, MP3, Vorbis or AC-3 pass-through (supports encoding of several audio tracks)
[/LIST]
 
**Misc features:**
 
[LIST]
[*]Chapter selection
[*]Basic subtitle support (burned into the picture)
[*]Integrated bitrate calculator
[*]Picture deinterlacing, cropping and scaling
[*]Grayscale encoding
[/LIST]
[/quote]
[/CENTER]

I personally find it very comfortable to use with a really simple GTK GUI that works out with even the most unexperienced users. It runs on both of my computers, a Vista desktop and a Ubuntu 9.04 laptop, and honestly, I couldn't ask for any better. Oh, and if you're concerned about the whole "windows-style converters", well, Handbrake for Linux is completely faithful to its Mac OS X and Windows older brothers. :P

---

### Post by Chronon on 2009-09-02
> **FakeOutdoorsman said:**
> 

[WinFF](http://winff.org) is worth trying.  You could also try [Sinthgunt](http://code.google.com/p/sinthgunt/).  I don't have any experience with these.

WinFF is a front end for ffmpeg.  I don't know anything about Sinthgunt.

There's also Mencoder, a counterpart to Mplayer.

---

### Post by ken_do_san on 2009-09-02
Try mobile media converter, google search it, when you have the home page scroll to the very bottom, there is an Ubuntu install there.

---

### Post by blackmail on 2009-09-07
Well i have used all the software suggested here, but Mobile Conversion Media did the job.
I must say i had some very funny moments trying to find a good converter:
1) at the sound part Gnome sound converter died, so i tried soundKonverter, and it works fine.
2) First video converters just gave errors, tried the installation and users guide on ffmpeg, did not work, or I was mentally challenged when I rad the documentation. avidemux was the funniest yet I have converted a flv video to avi, the conversion went through, and when i started the vid, a chipmunk version had been created, that was most odd, and then, expecting the worst, but still hoping for the best, i went on to google and searched for the last converter, installed it (but with serious doubts in mind seing the whole 9 MB of the installation file, and comparing to the 20-something mb size of the dreadded ffmpeg). Ok any way it passed the test and it works fine, so thank you all forr your kind help.

---

### Post by Revolutionary101 on 2009-09-07
Glad I could help

---

### Post by andrew.46 on 2009-09-07
Hi blackmail,

> **blackmail said:**
> Well i have used all the software suggested here, but Mobile Conversion Media did the job.

You might be interested to know that when you are using [mobile media converter]("http://www.miksoft.net/mobileMediaConverter.htm") you are actually using FFmpeg anyway :-).

Andrew

---

