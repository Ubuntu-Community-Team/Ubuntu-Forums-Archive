---
title: "MKV to Hardsubbed AVI..."
date: 2010-08-17
forum: Multimedia Software
---

### Post by Stigmata13 on 2010-08-17
Hello. I have a pretty large collection of videos, and a lot of them are anime shows in .mkv format, with english subtitles. I have an Xbox 360 but no matter how hard I've tried I haven't been able to figure out a way to stream them to the 360, as it doesn't support the MKV container.

The show I'm currently attempting to convert has .h264 video, .aac audio, and . a s s (without spaces) subtitles. From my understanding this is perfectly fine, and it can be put into an AVI or M4V container without re-encoding the video or audio stream. But that's where I run into some problems.

I use Ubuntu as my primary OS, so I prefer to use native linux applications. I need to: 1. Put the audio and video streams in an avi/m4v container, preferably without desyncing the audio/video or changing the framerate, and 2: convert said .a s s subtitles into hardcoded subs for the video, as Xbox 360 does not support softsubs. I am aware though that this will probably take re-encoding, but I'd like to do it without sacrificing the quality or changing the video framerate.

I've tried program Avidemux and Handbrake, but neither of these seemed to work. I'd be comfortable using the cli if I had to, or another program with a gui.

Anyone have any ideas?

Edit: On a side note, if anyone could teach me how to re-encode from the cli with as little headaches as possible, I'd be much obliged.

---

### Post by Bonster on 2010-08-17
Think u should try 'MKVToolNix' in the repo, to split the streams and subs, then go from there and use any container u wish to convert to

---

### Post by Stigmata13 on 2010-08-20
Nevermind, I figured it out. I'll try to elaborate on what I did just in case anyone is trying to figure out how to do this themselves.

My original video featured h.264 video along with .aac audio. But, in order to add the subtitles I had to use Avidemux, but Avidemux doesn't like h.264 (or so I take from the warning about losing frame accuracy.)

So to get around this, I converted the original .mkv video in handbrake, to an .M4V container using the FFmpeg codec. This resulting .M4V file would play fine on the 360, but it featured no subtitles.

The next thing I did was use MKVextract to extract the .a s s subtitles from the original .mkv file. Currently I'm using a GUI version I installed under wine, as I found it was faster than trying to learn the cli version.

From there, I downloaded a program called Aegisub. With this program, I was able to alter the font/size and even margins on the subtitles, to make sure they were my preferred size and to make sure they weren't cut off by overscan.

And finally, I loaded the raw .M4V video into a Qt version of Avidemux (The GTK version seems to have a bug) and converted the video stream using the MPEG-4 ASP codec, and copied the audio. Then, I was able to add the subtitles under "Filter", and the result was an .M4V file that would play on the Xbox 360 via network stream, with subtitles properly displayed.

---

