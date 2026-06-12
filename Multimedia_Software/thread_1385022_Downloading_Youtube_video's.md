---
title: "Downloading Youtube video's"
date: 2010-01-19
forum: Multimedia Software
---

### Post by pathfindermwd on 2010-01-19
In windows I used to use Real Player for downloading video.  A small realplayer tab above the video would allow me to download the video.  I have installed realplayer on Ubuntu
(it's listed under applications>sound and video), and of course have Adobe flash installed, but real player isnt working on firefox like on IE.  I cant find an option for it to attach itself to firefox like it does in IE.  I have re-started Firefox, and it was listed under add-ons plugins, though it's gone now.

Anyway, how can I download the video in Firefox/Ubuntu?

Thanks,

---

### Post by alwayshere on 2010-01-19
"download helper" is a firefox add on is what ya want

[http://www.downloadhelper.net/]("http://www.downloadhelper.net/")

---

### Post by psavva on 2010-01-19
> **alwayshere said:**
> "download helper" is a firefox add on is what ya want

[http://www.downloadhelper.net/]("http://www.downloadhelper.net/")

I agree. Downloadhelper is probably your best solution because you can even convert to different formats :D

---

### Post by VertexPusher on 2010-01-19
Flash videos get downloaded to the /tmp folder. Just copy them from there. No special tools required for that.

---

### Post by SumTingWong on 2010-01-19
> **VertexPusher said:**
> Flash videos get downloaded to the /tmp folder. Just copy them from there. No special tools required for that.

You may have have to add .flv at the end of the filename to get certain media players to play them.

---

### Post by pathfindermwd on 2010-01-19
Thanks guys.  I got it installed.  Weird though that when I downloaded the video in flv real Player wouldnt play it.  I thought that was realplayer's codec.  

I can't get the converter to work.  I tried to convert it to .avi and I get this pop-up window: 

Conversion requires an external application that appears to be missing on your system.
Configure conversion ?

I click on configure and in a prefrences window this is in red:  /usr/bin/ffmpeg

I don't know what it's wanting me to do in the preferences window.

---

### Post by ron999 on 2010-01-19
Hi
Whatever converter you're trying to use is telling you that it needs to be configured correctly.
If you're not sure how to do this use a simpler converter such as WinFF to convert it to avi.
Here's Winff:-[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by WillardTheGrey on 2010-01-19
I think this might be what your looking for [http://www.downloadhelper.net/conversion-manual.php#install-other](http://www.downloadhelper.net/conversion-manual.php#install-other)

---

### Post by VertexPusher on 2010-01-19
> **pathfindermwd said:**
> Weird though that when I downloaded the video in flv real Player wouldnt play it.  I thought that was realplayer's codec.
.flv = Flash video --> Flash Player
.rm = RealMedia video --> RealPlayer

These are entirely separate formats. In fact I was quite surprised when you said that RealPlayer for Windows would play YouTube videos. Certainly not through its own codecs.

> I can't get the converter to work.  I tried to convert it to .avi and I get this pop-up window: 

Conversion requires an external application that appears to be missing on your system.
Configure conversion ?

I click on configure and in a prefrences window this is in red:  /usr/bin/ffmpeg

I don't know what it's wanting me to do in the preferences window.
It wants you to install ffmpeg.

```
sudo apt-get install ffmpeg
```

But I'm curious: Why would you want to convert a low quality FLV file into an even worse AVI file? You can play the FLV files with any of Ubuntu's media players.

---

### Post by pathfindermwd on 2010-01-24
Thanks all, I got the video download all up and running with DownloadHelper. It works great.  Thanks again for all the help.

---

