---
title: "Are there any tools to convert MKV to MP4"
date: 2008-11-28
forum: Multimedia Software
---

### Post by jcadam on 2008-11-28
Hello,
Are there any tools in ubuntu can convert Mkv to Mp4. I just want to transfer some video files to my ipod.

---

### Post by 4kfooler on 2008-11-28
TRY HandBrake

---

### Post by dorkdork777 on 2009-01-07
Sorry to bump such an old thread, but [I found a guide]("http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml") that seems to work for this purpose. HandBrake seems OK, but the audio stutters a lot, and isn't in sync at all. This guide works fine, and you don't need to install AviDemux from SVN, as it says; just run:
```
sudo apt-get install avidemux
```
and the right version will be installed, and you can skip to "Convert a movie to PSP specific format".

---

### Post by wolfen69 on 2009-01-07
> **dorkdork777 said:**
> HandBrake seems OK, but the audio stutters a lot, and isn't in sync at all.

i hope this is not a blanket statement. handbrake has worked well for me on several computers and works well for other people as well. use what works best for you.

---

### Post by Straumoy on 2009-02-15
Hello,

what do you do in AviDemux if there isn't a separate subtitle file? According to the guide, you browse to the file in order to add it as a subtitle filter.

However I've rarely come over this type when watching anime. For the most part the subtitles seems to be part of the MKV file itself rather than a separate file.

I suppose the same issue would come if you were to use dual audio (english and japanese or whatever). How do you select which audio to use?

---

### Post by Zilioum on 2011-04-23
I was fiddling around for a long time with this .mkv to .mp4 problem, and now I've finally written a little program to take care of it. Here is the URL of the projects page on github:[https://github.com/Basphil/MKVToMP4Converter](https://github.com/Basphil/MKVToMP4Converter). 
Turning an .mkv file in an .mp4 file works well, it does check for the order of audio/video streams and chooses the right fps. 
You can additionally have it watch a directory for new .mkv files, and then it automatically converts them. I'm still working on this part, but for single .mkv files it works reasonably well.

There are still improvements to do (like delete the temp files etc.) but I hope that it can be of use to you.

---

