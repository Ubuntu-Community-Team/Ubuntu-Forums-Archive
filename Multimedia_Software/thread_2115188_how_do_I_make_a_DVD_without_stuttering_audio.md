---
title: "how do I make a DVD without stuttering audio?"
date: 2013-02-12
forum: Multimedia Software
---

### Post by blackdalek on 2013-02-12
I have a few source video files which all play fine as is.
I want to burn them to a DVD which can be played in a standard DVD player.
But no matter what I try, the conversion process never works and the video/audio is ruined.
I either get out of sync audio, silence or stuttering audio.
Video also gets corrupted to varying levels depending on settings, but that is not the major problem - I can live with a bit of pixelation here and there... it is the audio problem which is unacceptable.

The videos are all 16:9 ratio and play as such in movieplayer, but the pixel dimensions are 512px x 384px.

They are Matroska video files.
video codec is mpeg-2 video, 25fps
audio codec is mpeg-4 aac, stereo 44.1khz

How can I re-encode these files to be a usable DVD vob format, without destroying the audio?

please help me!

---

### Post by ieee488 on 2013-02-12
Sometimes it is the blank media that you are using.

---

### Post by blackdalek on 2013-02-12
> **ieee488 said:**
> Sometimes it is the blank media that you are using.


I haven't gotten as far as burning a DVD. I am always creating an image or folder on the hard disk first to test before burning.

---

### Post by ieee488 on 2013-02-12
In that case, I have no idea.

I use Windows XP for my very simple DVD authoring and burning needs.

---

### Post by speartip on 2013-02-13
I always get perfect results by doing the following:
Update to the latest ffmpeg using this ppa:
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
Then download the latest devede from here:
[http://www.devede.org/](http://www.devede.org/)
In devede's settings make sure the encoder for videos & menus is set to ffmpeg.
Also when you add the file you want to convert, under advanced options & quality, tick the box for "use dual pass encoding". This needs to be repeated for every file you add.
Then just burn the iso to dvd.

---

