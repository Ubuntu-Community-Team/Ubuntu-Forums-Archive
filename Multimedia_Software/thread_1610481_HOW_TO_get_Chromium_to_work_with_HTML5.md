---
title: "HOW TO get Chromium to work with HTML5"
date: 2010-10-31
forum: Multimedia Software
---

### Post by mrebanza on 2010-10-31
To get Chromium to work with HTML5 in uBuntu you have to first uninstall the free "open source only" package "chromium-codecs-ffmpeg" that ships with chromium (not chrome) with only supports OGG and WEBM video 


```
sudo apt-get remove --purge chromium-codecs-ffmpeg
```


and install the non-free proprietary version of the package named chromium-codecs-ffmpeg-nonfree  which has full support for MP3 and MP4 codecs . . . 

```
 sudo apt-get install chromium-codecs-ffmpeg-nonfree 
```


After searching and Google ing like crazy . . . I couldn't find the solution spoon feed to me but was able to figure out the issue with mp3 and mp4 html5 playback in chromium and figured I would spoon feed it to everyone else! Enjoy.

---

### Post by mrebanza on 2010-10-31
Also if you love speed like me . . . you should set plug-in to on-demand in chrome . . . so it will only load flash when you want it to . . . equivalent to NO-FLASH for Firefox but with out a plug-in . . . Enjoy.

---

### Post by sci-fi guy on 2010-11-05
> **mrebanza said:**
> Also if you love speed like me . . . you should set plug-in to on-demand in chrome . . .

And how do you do that?

---

### Post by mrebanza on 2010-12-28
> **sci-fi guy said:**
> And how do you do that?

unfortunately the latest update of chrome removed the feature to have "On-Demand" Flash Play-back . . . . IDK why but it is simple GONE . . . HTML5 and flash should still work with the methoid above still those . . . . you should / could always just install the commercially released [Google Chrome]("http://www.google.com/chrome") from [www.google.com/chrome](www.google.com/chrome) which not only supports html5 out of the box but also ships with the latest version of flash for linux pre-nstalled !!!!

---

