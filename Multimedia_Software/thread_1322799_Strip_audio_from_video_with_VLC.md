---
title: "Strip audio from video with VLC"
date: 2009-11-11
forum: Multimedia Software
---

### Post by captgadget on 2009-11-11
and VLC returned an error message:[COLOR="Red"]Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG Audio layer 1/2/3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.[/COLOR]

Any suggestions on where I go from here

---

### Post by andrew.46 on 2009-11-11
Hi captgadget,

> **captgadget said:**
> Any suggestions on where I go from here

The defailt version of FFmpeg is intentionally short of a few codecs. Have a look at this guide for an easy method to beef up your copy:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and hopefully this will enable the appropriate codec for vlc.

Andrew

---

### Post by captgadget on 2009-11-11
Worked perfectly!!!!!!!!!!!! Thank you

---

### Post by andrew.46 on 2009-11-12
Hi captgadget,

> **captgadget said:**
> Worked perfectly!!!!!!!!!!!! Thank you

Excellent news :).

Andrew

---

### Post by aseptilena on 2012-03-16
(SOLVED)

The other successful solution is using gnome-mplayer

We can type this in terminal :

sudo apt-get install gnome-mplayer:KS

---

