---
title: "video streaming problem"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by ijkn on 2007-06-30
Hi,

I have installed firefox  2.0.0.4 & mplayer plugin(3.31) with all the win32 codecs in kubuntu 7.04.  


Basically, all the video and audio files can be streamed except files with extension(.asx). I have attached a screen shot....the .asx files should be supported by the plugin & firefox. However, firefox seems can not recognise it. I am unable to stream the video clips in the following website:
[http://news.tvb.com/630pm/2007/0628/index.html](http://news.tvb.com/630pm/2007/0628/index.html)

When i click to play the video, it shows a pop up screen and ask me what to do ...download or open with....


Does anyone using firefox and mplayer plugin in kubuntu/ubuntu....is able to stream the video clips on that website? Thanks.

---

### Post by linuxwizard on 2007-07-01
Have you tried any other websites and see if you have problems. I tried your link it show connecting and than stops. Their might be a problem with that site. Myself that is the first website i could not play video on.

---

### Post by ijkn on 2007-07-01
thanks linuxwizard.

I have tried....the video clips(.asx) can be loaded using windows media player in MS windows xp and mplayer-plugin in fedora core 4....without any problems.

But I don't know why I can't make it to work in ubuntu/kubuntu.  ;)
In this case, Firefox seems does not pass the video automatically to the mplayer-plugin so the video can't be loaded. I have no idea on how to configure firefox so that it can load the files with extension .asx using mplayer-plugin. :(

---

### Post by RomeReactor on 2007-07-01
Hi. Look in Firefox's **Edit-->Preferences-->Content** and click the "Manage" button on the bottom; check if there's any action associated with ASX files, and if so, change it to open in mplayer.

---

### Post by ijkn on 2007-07-01
thanks RomeReactor.

In default, there's no action associated with ASX files.
I have already tried and changed it to open the file .asx with mplayer in 'Edit-->Preferences-->content--->file types" before...but still does not work.

Is there a way to configure firefox so that the file is opened with mplayerplug-in 3.31 instead of mplayer?  Just like the screen shot that is attached in my first thread....i can't make the file(.asx) to open with mplayer-plugin(instead of mplayer) manually in Edit-->Preferences-->content--->file types.

It seems that i post this to the wrong place. I think i should post this kind of topic in firefox or mplayer's forum

---

### Post by RomeReactor on 2007-07-01
I just tried playing a video from the site and it worked here. I use **totem-xine** with all the available libraries (**libxine1, libxine1-ffmpeg, libxine-extracodecs**), by the way. I'm attaching a screenshot of my download actions window; maybe that can help. Note that I also enabled wmv playback by installing the **w32codecs** through the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories.

EDIT: I just noticed you're running KDE; What plugin do you have for Firefox? Kaffeine?

---

