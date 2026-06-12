---
title: "Good Video Converter for Ubuntu? (Convert to MPEG 1/2 for Rockbox)"
date: 2009-06-29
forum: Multimedia Software
---

### Post by tomreid on 2009-06-29
Hi

I've been researching video converters for Ubuntu this afternoon. My problem was needing to convert some iPod compatible formats to MPEG 1 or 2, as these are the only formats that Rockbox supports.

I thought Handbrake may do it, but it doesn't. Tried briefly with VLC, but I find VLC difficult to use for anything other that playing media files. I came across FF Video Converter (WinFF) which seemed to be the answer, as I believe most of what I need to do I can do in a terminal window, but I am hopless at using the terminal and really like to use a GUI when I can. This programme even had a nice Rockbox preset for Rockbix, but all it did when i tried to use it was pull up the terminal, which then fired error messages at me. 

I finally found a post that said someone else had cracked this by running the free Windows app "Format Factory" in WINE. This is actually working for me, which is great as it's the first time I've got anything to work in WINE. There are one or two clitches, the programme's GUI does not display as normal, but it's useable.

So my question is, is there a native Linux app that will handle conversion of video formats like Format Factory? I always like to run native apps where I can.

cheers

---

### Post by skunkTrader on 2009-06-29
> **tomreid said:**
> but all it did when i tried to use it was pull up the terminal, which then fired error messages at me.
WinFF is just a front end to FFmpeg.  It would help if you could paste a copy the error messages that were displayed in the shell window -- that way somebody might be able to help.

---

### Post by little_penguin on 2009-09-16
Avidemux is a great piece of software for this purpose and is in the repositories.

---

### Post by andrew.46 on 2009-09-16
Hi tomreid,

> **tomreid said:**
> So my question is, is there a native Linux app that will handle conversion of video formats like Format Factory? I always like to run native apps where I can.

I downloaded Format Factory as I suspected that it could be yet another program that violated multiple licenses for programs such as FFmpeg and MEncoder. I was not surprised to find in the directory labelled FFModules multiple programs such as FFmpeg, MEncoder, mkvmerge, MPlayer etc etc that have been used *without* acknowledgement. I attach a screenshot to demonstrate this.

If you were keen to spend a bit of time learning to use the great program FFmpeg there is a starting point provided on these forums:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and IMHO time spent learning such a program far outweighs any benefits of using such programs as Format Factory.

Andrew

---

### Post by FakeOutdoorsman on 2009-09-16
Interestingly, Format Factory is a proud member of the FFmpeg [Hall of Shame](http://ffmpeg.org/shame.html).

---

### Post by BubbaBlues on 2009-09-16
Devede is the best converter I've ever used. :guitar: It's in the repos.

---

### Post by Darkwing-Duck on 2009-09-23
Here is another option for converting FFMEPG.

[http://gwos.org/udsf/doku.php/software:ffmepg:conversion](http://gwos.org/udsf/doku.php/software:ffmepg:conversion)

---

### Post by FakeOutdoorsman on 2009-09-23
> **Darkwing-Duck said:**
> Here is another option for converting FFMEPG.

[http://gwos.org/udsf/doku.php/software:ffmepg:conversion](http://gwos.org/udsf/doku.php/software:ffmepg:conversion)

Wow, that site looks similar to this one:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Chronon on 2009-09-23
> MPEGplayer is an MPEG video player viewer plugin. It is currently capable of playing back MPEG-1 and MPEG-2 video streams with MPEG audio multiplexed into .mpg files (MPEG Program Stream) and raw MPEG-1 and MPEG-2 video streams.

Some instructions are given here: [http://www.rockbox.org/wiki/PluginMpegplayer#How_To_Encode_Files](http://www.rockbox.org/wiki/PluginMpegplayer#How_To_Encode_Files)
For example:
[B]>  [LIST]
[*]Using WinFF (Windows / Linux) 
[*]Using ffmpeg (Windows / Linux / Mac OS X) 
[*]Using VLC (Linux / Mac OS X / Windows)
[*]Using Mplayer/Mencoder (Linux / Mac OS X / Windows)
[/LIST]
[/B]

WinFF should do the job just fine and is the most popular recommendation at the Rockbox forums.  I'm sure someone can help you get that sorted if you post error messages.

Alternatively, any conversion software that will convert to the right video and audio format (and allows you to set dimensions, etc.) should also work fine.

---

