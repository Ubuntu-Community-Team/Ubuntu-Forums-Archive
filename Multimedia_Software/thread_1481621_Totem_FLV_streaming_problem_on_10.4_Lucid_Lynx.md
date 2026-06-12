---
title: "Totem FLV streaming problem on 10.4 Lucid Lynx"
date: 2010-05-12
forum: Multimedia Software
---

### Post by dotBL0t on 2010-05-12
Hi guys! I'm experiencing a strange issue with streaming of FLV files with Totem. Before upgrading to 10.4, I used to streaming URL like this ***[http://hd.spaziogames.eu/hd20/2009/9/psp/4018.flv](http://hd.spaziogames.eu/hd20/2009/9/psp/4018.flv)*** with Totem. The player started buffering for 2 or 3 seconds and then I could watch the video. Now, on Lucid, it doesnt start. I just noticed that it creates a "totem-XXXXX" temp file on /tmp/ and then the video starts to play only after the whole file has been cached. Anyone is experiencing the same issue after upgrading?

[IMG]http://www.imagebanana.com/img/3y29mni/Selezione_009.png[/IMG]

Bye!

---

### Post by LarryMi on 2010-05-12
Even though I couldn't understand a word, the video via totem worked perfectly.  Not sure if its because I'm running 64 bit or not.

I have begun to appreciate Totem very much and hope someone can answer a question.  If I watch a video such as an [Apple Movie Trailer]("http://trailers.apple.com/trailers/wb/jonahhex/"), and choose 1080p, the size of the window does not change even though I have set in the Preferences "Automatically resize the window when a new video is loaded".  If I previously choose 480p or 720p and then 1080p, the size of the window remains the same.

It seems Totem can only reproduce a certain level of definition and does not recognize anything  beyond that.

Any info is appreciated.

---

### Post by dotBL0t on 2010-05-13
> **LarryMi said:**
> Even though I couldn't understand a word, the video via totem worked perfectly.  Not sure if its because I'm running 64 bit or not.

I have begun to appreciate Totem very much and hope someone can answer a question.  If I watch a video such as an [Apple Movie Trailer]("http://trailers.apple.com/trailers/wb/jonahhex/"), and choose 1080p, the size of the window does not change even though I have set in the Preferences "Automatically resize the window when a new video is loaded".  If I previously choose 480p or 720p and then 1080p, the size of the window remains the same.

It seems Totem can only reproduce a certain level of definition and does not recognize anything  beyond that.

Any info is appreciated.
The video works perfectly via Totem for me too. But only after the whole video gets downloaded. I mean, I open the stream with the "Open location..." and set the URL as source, then the player starts caching the file but the video won't start until it gets 100% cached. It doesnt happen with WMV or MP4 videos...It just take 2 or 3 seconds for buffering and then the video starts playing.

---

### Post by bgruber on 2010-06-03
i've noticed this problem too, filed it as a bug: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/589012](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/589012)

/brian

---

