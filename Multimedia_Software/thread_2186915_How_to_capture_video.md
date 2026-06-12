---
title: "How to capture video?"
date: 2013-11-09
forum: Multimedia Software
---

### Post by johnaaronrose on 2013-11-09
I'm using Ubuntu Precise 64 bit. Is there an app which will capture video & audio from a TV programme being played on my PC? I'm thinking of the video coming from Channel4 or 5 on Demand.
PS by capture, I mean record to disk.

---

### Post by TheFu on 2013-11-10
It depends.
Mainly on the physical device used to capture the TV.  Look at the devices supported by MythTV as a start.

In general ...
* capturing the stream is best.
* snapping the video on the screen is the worst and will eat CPU - often more CPU than available.
* the source resolution is critical - capturing 640x480 is relatively easy. 1080p can be very hard even on Core i7 hardware without an addon card/device.
* the source of the video matters.  Cable/broadcast TV have lots of solutions.
* I don't know what channel4 is, sorry.  If it is a web-based/internet TV ... they probably use DRM, so the specific DRM will need to be broken. I can't help with that.
* The physical connection from the source device matters. HDMI usually includes HDCP - most of the time, if you are using an external device like this, then looking for a setup used by HiDef gamers to capture their gameplay would be a start.  Many of these solutions use the _analog hole_ to capture video. I do not believe that any of these work on Linux until $500+ is spent and professional production equipment is used.

* There are screen capture programs ... look for "screencasting"  [http://www.linux.com/learn/tutorials/745745-how-to-make-a-youtube-instructional-screencast-video-on-linux](http://www.linux.com/learn/tutorials/745745-how-to-make-a-youtube-instructional-screencast-video-on-linux) might help.

Sorry - started down a rabbit hole that probably doesn't apply to your needs.

---

### Post by johnaaronrose on 2013-11-11
Channel 4 & 5 on demand are websites where TV programmes (previously broadcast by those channels) can be replayed on screen including audio. I've previously tried RecordMyDesktop but it replays the video without sound. Presumably this is to allow you to add your own sound e.g. when making your own Youtube video when you would add your commentary through a microphone. However, I've just now used Kazam and it allows recording of the audio (onto a .mp4 video file) using 'Monitor of Built-in Audio Analogue Stereo'  for the 'Audio Source 1' parameter.

---

### Post by TheFu on 2013-11-11
So it is like abc.com, cbs.com, wb.com, tnt.com, hulu.com, crackle.com, vimeo.com .... netflix.com ... plus any of the basic cable channel streaming ... 

In the USA, those sites have switched to Flash+DRM (plus whatever netflix does), to prevent stream capture unless it is encrypted. I have never found recording software that worked acceptably without a hardware component.

So, does Kazam work and should this thread be marked solved?

---

### Post by thesleash on 2013-11-21
perhaps avconv

---

### Post by johnaaronrose on 2013-11-22
I'm using ffmpeg (not the version supplied with Ubuntu, which is a copy of avconv, as that's buggy) but the original. If anybody wants to know how to install that, please Pm or post here. I'm just about to start writing a Gambas-based GUI for the required ffmpeg calls (which are complex) as the existing ones (LiVES & eidete) have problems.

---

### Post by thesleash on 2013-12-02
the following command worked for me.


ffmpeg -f video4linux2 -channel 1 -i /dev/video0 -f alsa -i default -qscale 8 -vol 86 -crf 10 -ar 44100 -threads 1 -vf yadif,scale=720:406,scale=iw/1.075:-1 -y out.mpg


as proof here's a link to one of my youtube channels.


[http://www.youtube.com/user/thesleash](http://www.youtube.com/user/thesleash)

---

### Post by philinux on 2013-12-02
You can also use vlc to capture screen.

[http://www.howtogeek.com/120202/](http://www.howtogeek.com/120202/)

Choose an appropriate frame rate.

---

### Post by philinux on 2013-12-03
Here's a new one on me. Vokoscreen.

[http://linuxg.net/how-to-install-vokoscreen-1-7-0-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-16-15-14-13-pear-os-8-7-and-elementary-os-0-2/](http://linuxg.net/how-to-install-vokoscreen-1-7-0-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-16-15-14-13-pear-os-8-7-and-elementary-os-0-2/)

---

### Post by BenjaminCHILOE IS. on 2013-12-03
Hello John,

Have you tried this one : [http://www.maartenbaert.be/simplescreenrecorder/](http://www.maartenbaert.be/simplescreenrecorder/) ?  

The best.

---

