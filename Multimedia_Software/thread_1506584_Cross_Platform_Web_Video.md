---
title: "Cross Platform Web Video"
date: 2010-06-10
forum: Multimedia Software
---

### Post by Alan James on 2010-06-10
Does anyone know of a way of embeding video into web pages that can be viewed on multiple platforms; Windows, OS X, Linux, iOS, Android?

Quicktime only works on Windows, OS X, and iOS.

Flash only works on Windows, OS X, Linux, and Android. However, it does not run well for Android.

Is there a better solution?

(This is really a web design question but I have found the Ubuntu community to be smarter than most web design communities out there)

---

### Post by FakeOutdoorsman on 2010-06-10
> **Alan James said:**
> Does anyone know of a way of embeding video into web pages that can be viewed on multiple platforms; Windows, OS X, Linux, iOS, Android?

Quicktime only works on Windows, OS X, and iOS.

Flash only works on Windows, OS X, Linux, and Android. However, it does not run well for Android.

Is there a better solution?

(This is really a web design question but I have found the Ubuntu community to be smarter than most web design communities out there)

I currently use H.264 video and AAC audio in a MP4 container.  I use JW Player as a flash player on the web page. See the [Is there a codecs / media formats for Dummies?](http://ubuntuforums.org/showpost.php?p=8756850&postcount=5) thread for encoding examples and more details on this method.  Another good Flash player is Flowplayer.

This method of course doesn't cover everything, but you could use JW Player 5.2 Beta to provide either H.264 in Flash or the new WebM format in a HTML5 video tag.  I believe this player will fallback to whatever format is accepted by the platform/browser/device, but I haven't tried it myself.  It might be worth a try and I'd be interested in hearing how it works for you.  To encode to WebM, follow this guide (it's currently missing *libvpx* installation, which is needed for VP8/WebM, but I'll add it in a few miutes):

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

A Simple and Basic Example Command (I'm still learning how to use this format, FFmpeg development is very active as usual, and everything is still very "green"):
```
ffmpeg -i input -threads 4 output.webm
```
You have to manually choose an appropriate number of threads for your CPU or omit this option completely.  Other options to consider are multiple passes and different rate control methods.

Required Reading for WebM & Friends:
[list][*] [Google's VP8/WebM and What it Means for You](http://www.longtailvideo.com/support/blog/12120/the-google-vp8webm-announcement-what-does-it-mean-for-you)
[*] [JW Player for HTML5](http://www.longtailvideo.com/support/jw-player/jw-player-for-html5)
[*] [The first in-depth technical analysis of VP8](http://x264dev.multimedia.cx/?p=377)[/list]

---

### Post by Alan James on 2010-06-12
Thanks. I will look into this in the next few days.

---

