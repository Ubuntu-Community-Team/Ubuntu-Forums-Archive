---
title: "Fresh Player or PipeLine?"
date: 2015-08-13
forum: Multimedia Software
---

### Post by jjmgray on 2015-08-13
I don't like Flash but it's pretty necessary for using a lot of the  internet. However, it seems that the version of Flash found in Firefox  for Ubuntu is out of date, and it fails pretty hard for pretty much  anything but YouTube in my experience.
I tried using Opera but it  seems to be causing complete freezes of my computer when I use it and I don't want to use Chrome.

I'm aware of two alternative to native Flash, as per the title, which would you recommend?

---

### Post by Yellow Pasque on 2015-08-13
I build my own Freshplayer (on Debian), and it works well. I don't use a ton of Flash though.

---

### Post by monkeybrain20122 on 2015-08-13
Freshplayer works more seamlessly but it doesn't work with certain drmed streams (neither does chrome on Linux). pipelight works for these but being a wine wrapper it doesn't integrate as well and probably breaks things like buttons and menus on some sites. I don't watch drmed stream so I use freshplayer (I compile from source but you can get it from webupd8's ppa) Actually I don't use flash that much. The firefox mpv addon plays most flash videos without flash and works better than both flash and html5 especially on weaker machines when it does work.

---

### Post by efflandt on 2015-08-13
I would recommend Google Chrome browser (from Google itself). [http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha&utm_term=chrome](http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha&utm_term=chrome)

They have deb versions in 64 or 32-bit that work in Ubuntu. It includes their own Pepper Flash which is the same version as Windows flash (currently 18.0.0.233). It does Netflix without having to use wine (but I think you need to set your preferences on Netflix website to "Prefer HTML5"). And you can install Chromecast Extension to stream to a Chromecast device. Not sure how different that is from related Chromium browser in Ubuntu repositories. One thing it apparently does not do is streaming "protected content", but I am not quite sure what that is and it has only affected 1 series of shows on Hulu (the error recommends Firefox, but Linux Firefox 40.0 apparently cannot do that either).

Although, my default browser if Firefox with whatever Linux version flash is installed/updated by flashplugin-installer.

Currently running 64-bit Ubuntu 14.04 with nvidia graphics.

---

### Post by mc4man on 2015-08-13
> **monkeybrain20122 said:**
> . The firefox mpv addon plays most flash videos without flash and works better than both flash and html5 especially on weaker machines when it does work.
Just noticed something re: plugin. If ffmpeg used by mpv  is built with --enable-librtmp that opens up some sites that previously didn't work here (like cbs news videos > ones that have the mpv option, ie. 'featured videos'
Generally ffmpeg (shared) is  built with that enabled..
( also allows mpv itself to work, reports an error, then plays anyway

---

### Post by Yellow Pasque on 2015-08-13
> **efflandt said:**
> I would recommend Google Chrome browser

OP said s/he didn't want to use Chrome. Not everyone likes Chrome's interface and it's not exactly the most privacy-friendly browser [https://en.wikipedia.org/wiki/Google_Chrome#User_tracking](https://en.wikipedia.org/wiki/Google_Chrome#User_tracking)
Unless one needs support for DRM'd Netflix and such, it would be better to use chromium over Chrome anyway.

---

### Post by monkeybrain20122 on 2015-08-13
> **mc4man said:**
> Just noticed something re: plugin. If ffmpeg used by mpv  is built with --enable-librtmp that opens up some sites that previously didn't work here (like cbs news videos > ones that have the mpv option, ie. 'featured videos'
Generally ffmpeg (shared) is  built with that enabled..
( also allows mpv itself to work, reports an error, then plays anyway

Yes, also works on these apparently [http://www.cbs.com/watch](http://www.cbs.com/watch). I tested for a few, some work (e.g 48 hrs) others don't but the ones that don't work have regional restriction (see a no access message if load flash) and I am not in the U.S. So I think may be they would work too if you are in the U.S.

---

### Post by jjmgray on 2015-08-15
> **monkeybrain20122 said:**
> The firefox mpv addon plays most flash videos without flash and works better than both flash and html5 especially on weaker machines when it does work.
I'm not familiar with the mpv addon, but I'll look into it. :)

---

### Post by monkeybrain20122 on 2015-08-15
> **jjmgray said:**
> I'm not familiar with the mpv addon, but I'll look into it. :)

[https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/)

To use you need up to date mpv and youtube-dl from ppas (not from Ubuntu's stock repo, they are old/broken) Details here [http://ubuntuforums.org/showthread.php?t=2286848](http://ubuntuforums.org/showthread.php?t=2286848)

---

### Post by SeijiSensei on 2015-08-16
I've taken to using the Windows version of FlashPlayer in Firefox via the [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") extension to avoid any issues about versions. I originally installed pipelight to watch Netflix via Silverlight, but I since expanded it to handle Flash as well.

---

### Post by monkeybrain20122 on 2015-08-17
pipelight may be a bit sluggish if machine has weak cpu. I find it using more cpu than system flash, but freshplayerplugin uses hardware acceleration and performs better than system flash (on amd netbook freshplayerplugin has the additional option of using vdpau decoding and not just on Youtube,--which now default to html5 anyway. But on some rare sites may need to be tured off. But hd acceleration can be enabled without vdpau, still works a lot better than system flash on this netbook) But of course mpv is the best performance wise when it works.

---

### Post by mc4man on 2015-08-17
If using vaapi then freshplayer can fail with hwdec enabled (off by default), may depend on vaapi/libva version..

---

### Post by monkeybrain20122 on 2015-08-17
> **mc4man said:**
> If using vaapi then freshplayer can fail with hwdec enabled (off by default), may depend on vaapi/libva version..

It mostly works here except for a few sites (actually only two Canadian tv stations from what I tested) and embedded facebook videos (becomes pixated) Can always turn off vaapi in config file while still using some kind of hardware acceleration which still uses less cpu than flash 11.2.

---

### Post by jjmgray on 2015-08-20
I Installed pipelight, and silverlight and flash, and enabled them, but they still aren't working--they don't even show as installed. Don't see anything in the pipelight help section.
Any ideas?

---

### Post by monkeybrain20122 on 2015-08-20
> **jjmgray said:**
> I Installed pipelight, and silverlight and flash, and enabled them, but they still aren't working--they don't even show as installed. Don't see anything in the pipelight help section.
Any ideas?

Close FF and run this

```

sudo pipelight-plugin --create-mozilla-plugins

```

---

### Post by jjmgray on 2015-08-20
> **monkeybrain20122 said:**
> Close FF and run this

```

sudo pipelight-plugin --create-mozilla-plugins

```

That worked perfectly, thanks. :)

Through all of this I got to wondering, is it possible (in Linux) to use a media player like MVP or VLC to stream content, instead of just just videos of set length like on youtube?

---

### Post by SeijiSensei on 2015-08-21
All videos have a "set length" unless you're talking about something like a surveillance camera.

SMPlayer comes with a YouTube add-on.  There are also add-ons to play videos in the Firefox browser with a third-party engine.  I've used **gecko-mediaplayer** for that purpose, though I generally only watch streaming videos in Flash or Silverlight.  For video files on my system, I prefer native SMPlayer with the mpv engine.

---

