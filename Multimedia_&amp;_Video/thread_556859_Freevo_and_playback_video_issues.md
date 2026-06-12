---
title: "Freevo and playback video issues"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by samuraix51 on 2007-09-21
I am trying to setup freevo to be my media box I am having issues with the video quality and cropping of files playing in it though.

I am using mplayer to play the videos using the following command, as setup in /etc/freevo/local_conf.py
[color=green]mplayer -cache 5000 -idx -zoom -fs -ao oss -ac htdts,hwac3,a52,mp3[/color] file.avi

The videos in freevo look washed out (not as sharp), and are cropped incorrectly for what they should be.

When I run the same command on the command line not through freevo, the video looks sharper and the correct size like they should be.

I've also tried playing the files on a Windows XP box and they work correctly like they are supposed to.

Anyone have any ideas as to what might be causing this and how to fix it?
Any help would be much apprecated.

The files I'm testing with are:
Video: x264
Audio: AC3
Bitrate: 1500

---

