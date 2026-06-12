---
title: "Vimeo embeds not working on Firefox"
date: 2013-11-03
forum: Multimedia Software
---

### Post by jryan1971-4 on 2013-11-03
most of the videos played on these sites are Vimeo embeds 

[http://cytu.be/r/fullmoviesonyoutube](http://cytu.be/r/fullmoviesonyoutube)
[http://cytu.be/r/justmovies](http://cytu.be/r/justmovies)

Some are youtube embeds, but most are Vimeo embeds

I can watch the youtube embeds with Firefox
I can watch both youtube and Vimeo embeds with Chromium
But watching Vimeo embeds with Firefox is hopeless.  I get about 1 frame every 5 seconds and no audio.

Someone said it might have something to do with HTML 5.

Does anyone have any suggestions or is anyone able to successfully view the vimeo embeds in Firefox ?

Using Shockwave Flash 11.2 r202, Ubuntu 13.10

---

### Post by warp99 on 2013-11-03
Vimeo videos are hit and miss with Chromium and Firefox because both use the Adobe flash plugin, which is deprecated. If you install Chrome direct from Google with the "Pepper" flash plugin Vimeo videos will play without a problem:

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

This will also add the Google repository to your sources.list so updates will be available through the Ubuntu Software Updater. You can remove Chromium once Chrome is installed since it's redundant:

```
sudo apt-get remove --purge chromium*
```

---

### Post by jryan1971-4 on 2013-11-04
thanks

---

