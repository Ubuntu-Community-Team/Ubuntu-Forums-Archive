---
title: "problem with x264"
date: 2011-09-24
forum: Multimedia Software
---

### Post by januszmk on 2011-09-24
Hello.
Sorry for my English.
I have problem with playing a movie in x264. Some times on the movie strips are jumping. I think it's because I am using hd3000 on my i5 2500k. If it's true, is there some way to eliminate this strips? I tried mplayer/smplayer, vlc, and I tried change output drivers, but it didn't help. I have kubuntu 11.04.
I would be grateful if you could help me.
Janusz

---

### Post by nahuel_89p on 2011-09-24
It seems that you have installed X264 but it doesn't work right.
Are you using compiz or metacity? Does it happen with all sort of videos (coded with other codecs)? 

Try reinstalling H264. I followed the steps i quoted in this thread [http://ubuntuforums.org/showthread.php?t=1848761](http://ubuntuforums.org/showthread.php?t=1848761) and H.264 works perfect to me.

---

### Post by januszmk on 2011-09-25
It's happening with and without compiz. It didn't happened with xvid yet, I tried to reinstall x264 codec like in that thread. Maybe that's happening because I am using integrated graphics with my CPU?

---

### Post by nahuel_89p on 2011-09-25
I don't know! :S

---

### Post by FakeOutdoorsman on 2011-09-27
x264 is a H.264 encoder, not a decoder, so it will not help you play back any videos.

---

### Post by januszmk on 2011-09-28
> **FakeOutdoorsman said:**
> x264 is a H.264 encoder, not a decoder, so it will not help you play back any videos.

I know, This is happening in 720p mkv movies. I didn't tried other high quality format, I will try on weekend. I will try then play on windows to check if this is because of hd3000 or some drivers for linux

---

### Post by januszmk on 2011-09-29
I checked xvid, this same effect. I installed even kernel 3.0 from sources, but it didn't help. Any ideas?
With desktop effects, I have ~47 fps on 1920x1080, when I turn on a movie, then I get 37 fps

Edit: I just notice then this is not happening just on the movies, on some website, when I scroll some web sites slow, then I get the same effect

---

### Post by mlissner on 2011-11-20
Hi, I have the same thing on a Sandy Bridge integrated graphics chip. When I'm using the computer, occasionally bits of black corrupted screen will appear in little squares here and there.

Usually, if I scroll the window so the pixels are refreshed, the black squares get flushed away.

---

