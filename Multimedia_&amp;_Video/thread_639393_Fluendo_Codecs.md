---
title: "Fluendo Codecs"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by 6205 on 2007-12-13
It's almost a year now, that Fluendo released their fully legal, properly licenced native linux multimedia codecs based on gstreamer framework, but when i Google for some 
kind of review, nothing is there...

Don't tell me that nobody is interested on these products. For example "Complete set of playback plugins" for 28 euro sounds reasonable for me and probably could make Totem Gstreamer with Firefox plugin fully usable without Xine, Mplayer + plugin and without stolen M$ w32codecs...

What am i asking here is, have somebody experiences with these codecs ? How they work on default Ubuntu installation without Medibuntu or "restricted" multimedia packages ??? Do they provide flawless playback/streaming of Windows Media or Mpeg in default Totem-Mozilla Gstreamer plugin ? How is the overall instalation process ? 
Is it throught terminal or some kind of gui installer ? Or it's maybe a simple copy-paste libraries job...I want some answers, and i want them now :-)

[https://shop.fluendo.com/product_info.php?products_id=42&osCsid=v9blq08ktf0m96ndvdcmdhlg15](https://shop.fluendo.com/product_info.php?products_id=42&osCsid=v9blq08ktf0m96ndvdcmdhlg15)

---

### Post by mjukr on 2007-12-17
There are 5 reviews on that specific page, but I don't see anything related to Ubuntu...

So, why don't you be the first brave soul to drop 28eur and report back to the forums? :)

---

### Post by 6205 on 2007-12-18
> **mjukr said:**
> There are 5 reviews on that specific page, but I don't see anything related to Ubuntu...

So, why don't you be the first brave soul to drop 28eur and report back to the forums? :)

Okay, i have buyed them and downloaded...But currently i dont have Ubuntu installed.
I must wait and propably tomorrow i will check it on fresh, clean Gutsy installation...yai :-)

Uhm...i have attached extracted documentation from downloaded archive (4.3 MB unzipped).
Installation looks very easy. Hopefully it was worth the money, but i don't believe in miracles.

Anyway - we will see tomorrow...

---

### Post by mjukr on 2007-12-18
Cool!!! I look forward to your report! I might get these myself, although I have mixed feelings about proprietary formats. But we live in the real world and ogg/theora just does not get the job done right now... And I am in the US and don't like using "legally questionable" codecs/libraries...

---

### Post by mjukr on 2007-12-19
By the way, looks like Dell has incorporated LinDVD for legal DVD playback (US) on their newest Ubuntu system builds:

[http://direct2dell.com/one2one/archive/2007/12/18/38935.aspx](http://direct2dell.com/one2one/archive/2007/12/18/38935.aspx)

---

### Post by 6205 on 2007-12-19
> **mjukr said:**
> By the way, looks like Dell has incorporated LinDVD for legal DVD playback (US) on their newest Ubuntu system builds:

[http://direct2dell.com/one2one/archive/2007/12/18/38935.aspx](http://direct2dell.com/one2one/archive/2007/12/18/38935.aspx)

Uhm...yes i saw it 20 min. ago with video interview :-)

---

### Post by 6205 on 2007-12-19
Regarding those fluendo codecs. They works almost without problems. Everything in that megabundle is simple copy-paste "instalation" and that's all. But problem is somewhere else...I will try to explain (with my limited english...)


**1./ **Totem Mozilla Gstreamer plugin have very poor support for buffering - and that's a big problem for me or you or for million other average users. Playback works well, picture is sharp, sound clear, but you must have very fast internet connection, because if you have for example only DSL 1536 like me, you will be in many cases dissapointed.

If i want to see some large quality movie or game trailer, totem plugin every few seconds stops and buffers video and it's very disturbing. If it only could work like mozilla-mplayer plugin, that would be a different story because mplayer plugin is fully configurable. 
If i set buffer cache at 4096kb and 30% he first buffers and when he reaches my settings, playback follows, but also buffering continues _in background_ and that make a major difference in overall playback experience...
I wish totem mozilla plugin could work same way (*do you hear GNOME developers ?*)


**1.1/** Fluendo codecs don't works at 100% (i know, this is linux not windows) but even if you buy Megabundle or only Windows Media bundle, don't expect that Windows Media will work at 100% I have tried many webpages, almost everything is working great (with buffering issues related to totem plugin) - game/movie trailers, various news pages but i found on some porn sites that some WMV media files don't work...This could be (i don't know) because Fluendo codecs are propably suporting only Window Media 9, not 10 format. On this pages totem plugin dont works, but when i open this link in regular Totem Movie Player - Easy Codec Installation pop-ups and want to install some aditional codecs like gstreamer ffmpeg or bad or ugly versions...(frak)


**1.2/ **So currently the same and even better playback you will get when you install from repositories free ubuntu-restricted-extras + fluendo-mp3 packages. You will get with these also QuickTime movie playback support - but you will _still_ have problems with potential slow internet connection due lack of better buffering in Totem Mozilla Gstreamer plugin.


**2./** Ehm...so if you want objectively best possible playback experience with streaming videos in various formats and quality, only really very good (but not excellent) solution is mozilla-mplayer plugin + depencies + w32codecs. You may also need x264 package and some matroska stuff for HD videos in MKV (matroska container) files and you are done... 


**3./** Conclusion (or something like that) >>> Fluendo Codecs are very high quality - but...

...but linux applications are mostly not (totem-plugin) so if you want, you can give them a try but currently is simply much better solution to stick with mplayer + firefox plugin for best possible playback/streaming experience...


**[COLOR="Red"]EDIT >>>[/COLOR]** This review applies only for old version of Fluendo Codecs. Recently updated version is much better, highly recommended and also streaming with Totem plugin work much better....hmmmm :)

---

### Post by 6205 on 2008-01-28
You are receiving this mail to inform you that the Fluendo product you bought has been updated...


**Here are the details on updated products :**

- Windows Media Video now supports Windows Media 7 and 8 on top of
previously supported formats Windows Media Video 9 and VC1.
Additionally this codec has received a lot of optimization love which
makes it possible to play big HD clips on smaller hardware. 

- Windows Media Audio now supports Windows Media 10 and Windows Media
Speech on top of previously supported formats Windows Media 7, 8, 9,
Pro and Lossless. This codec has been optimized and consumes almost
50% less CPU.

- MPEG2 Video decoder has been optimized to reach similar performances
than other competing decoders

- H.264/AVC and AAC have been added to the Complete set of playback plugins. 
You can now playyour AAC songs or watch QuickTime movies using a highly optimized 
set of decoders for those formats.

- MMS network source has been thoroughly tested with a lot of Internet
streams. Lot of improvements were done to support as much streams as
possible.

Fluendo's team wishes you a happy new year for 2008.

Best regards, Fluendo Support Team , FLUENDO S.A.



**_[COLOR="Red"]LOOKS FRAKING AWESOME, I LOVE YOU GUYS[/COLOR]_** :guitar:

---

### Post by JGJones on 2008-01-28
Here's a summary of what the complete codec pack would give you (it also list what they sell, so if you want one of them you can get it on its own for a lower price) and as noted above - they have been optimised and improved to use less CPU etc. I bought mine nearly a year ago (as they would be bringing legal and supported codecs to Linux and they're a Linux company, so I wish to support them that way instead of just using the w32codec pack).

My experience of their codecs have been positive generally, ie videos play better than before etc in Totem and is to the point where I actually prefer using Totem over mplayer with w32codecs.

I do not know what do I need to do to measure performance impact - I have a dual core 2 2.2GHz with 4Mb cache and 2GB of ram, so performance isn't an issue for me.
What's available in Complete Set Pack:

Windows Media Audio Decoder (Windows Media 7, 8, 9, 10, Pro, Lossless and Speech)
Windows Media Video Decoder (Windows Media 7, 8, 9 and VC1)
Windows Media ASF Demuxer
Windows Media MMS Networking

MPEG2 Video Decoder
MPEG4 Part 2 (DivX) Video Decoder
H.264/AVC Video Decoder (32 bits only)
MPEG2 Program Stream and Transport Stream demuxer
MPEG4 ISO Demuxer
MP3 Audio Decoder
AC3 Audio Decoder
AAC Audio Decoder (32 bits only)

---

### Post by 6205 on 2008-01-29
> **JGJones said:**
> ....I bought mine nearly a year ago (as they would be bringing legal and supported codecs to Linux and they're a Linux company, so I wish to support them that way instead of just using the w32codec pack).

My experience of their codecs have been positive generally, ie videos play better than before etc in Totem and is to the point where I actually prefer using Totem over mplayer with w32codecs.

I do not know what do I need to do to measure performance impact - I have a dual core 2 2.2GHz with 4Mb cache and 2GB of ram, so performance isn't an issue for me....

I will test this new updated version propably through weekend, however they looks very good now...I agree to support this company and also other linux user should consider to donate/support them, because these codecs are crucial to wider linux adoption in home and no other free/restricted alternative is better. Best software must 
be propably proprietary. Serious development costs real money/time and can not be allways free of charge :-(

---

### Post by 6205 on 2008-01-31
Uhm....testing :)

---

### Post by yotux on 2008-02-10
Some site will not work if that are in windows media format.  From what I have read in the past in regards to wmv file some have drm on them.  The porn site that you talked about most likely using drm to protect there content from being downloaded and saved.  With the drm you would need to communicate to there server every time you wanted to view the video to make sure you license to the content was permitted.

Long story short if the windows media file has DRM it will most likely not work.  Microsoft has not given us the access to decode DRM content at this point in time.

Nathan aka Yotux

---

### Post by 6205 on 2008-03-05
> **yotux said:**
> Some site will not work if that are in windows media format.  From what I have read in the past in regards to wmv file some have drm on them.  The porn site that you talked about most likely using drm to protect there content from being downloaded and saved.  With the drm you would need to communicate to there server every time you wanted to view the video to make sure you license to the content was permitted.

Long story short if the windows media file has DRM it will most likely not work.  Microsoft has not given us the access to decode DRM content at this point in time.

Nathan aka Yotux

Hmm....interesting, i haven't thought about that, but i don't really care about DRM, because recently updated Fluendo codecs are exellent quality anyway and i have not get any other problems with streaming videos anywhere on web :) IMO it's now better than mozilla-mplayer plugin, with better picture/sound quality also on Quicktime trailers...

---

### Post by geoken on 2008-05-05
I want to try these to see if they'll improve gstreamer h264 mkv performance. Usually I'd just switvh to XINE, but I want to be able to watvh my movies in Elisa which only supports gstreamer.

---

### Post by JGJones on 2008-05-06
Biggest issue with codecs...

I've noticed that I've not been able to show up subtitles that's encoded within a MPEG2 file - for example in UK, I make recordings off BBC or ITV or whatever with MythTV.

It's a MPEG2 file.

GStreamer + Totem plays this just fine.

But I cannot show subtitles - VLC can do this (press K to show subtitles) (mplayer can't show subtitles either).

I do not know if this is a gstreamer issue or a codec issue? I would log a bug about this, but I would need to know where to do it first - ie with gstreamer or with codec! :)

Cheers

---

### Post by Lokken on 2008-05-07
I've purchased the megabundle, or whatever it's called not too long ago.

I must say, they're pretty nice, and very convenient.

My one beef is that either gstreamer or the AC3 codec (or a combination of both) seem unable to produce surround sound. It may just be Totem ignoring the 5.1 setting in the 'Audio' portion of the Preferences window.

I just want AC3 5.1 content to be played back properly, and I don't want to hear 2 channel content from more than 2 speakers (no .asoundrc w/ duplication etc).

If anyone knows how I can get 5.1 sound via gstreamer and the Fluendo codecs (using Totem), please share it with the rest of us.

Lokken.

---

### Post by gerymate on 2008-05-17
I have the MPEG Bundle, but this seems to be not enough to play back FLV videos (Youtube & sisters & brothers). I tried with one of the free Flash players Ubuntu offers as Macromedia Flash alternatives. There is sound (supposed to be MP3), but no picture.

Anyone have likely conditions? Anyone having some success with this?

---

