---
title: "Converting .avi to .mp4"
date: 2011-12-04
forum: Multimedia Software
---

### Post by ubunwhat on 2011-12-04
Forgive my ignorance of all things video. I have an Insigna Blu Ray player that normally plays .avi movies just fine from a USB.  For whatever reason I have one movie that it simply will not play.  It is a .avi and it plays perfectly in movie player on my ubuntu laptop, but the dvd player throws an unsupported file type message.  I'm wondering if I can just convert this to .mp4 quickly, which is another format that I know the blu ray player accepts.  Is there a way to do this quickly in Ubuntu?

---

### Post by andrew.46 on 2011-12-04
The problem will probably be one of the codecs in the avi container. Can you have a look at the codecs in your successful video and compare with the codecs in the failed video? Something like mediainfo should do or even have a look with vlc (under Tools --> Codec Information).

---

### Post by ubunwhat on 2011-12-04
Again, pardon my ignorance.  Medianinfo?  I don't see that in the repository.  And I don't see Vic either.  Can you explain that a bit for me, please?

---

### Post by ubunwhat on 2011-12-04
Just by clicking properties I can see that the avis that do play with no problem are XVID MPEG-4.  The one that is not playing nicely is DivX MPEG-4 Version 5.  I have begun converting to mp4 using Handbrake.  Is this a waste of my time?

---

### Post by MoreOrLess on 2011-12-04
> **ubunwhat said:**
> Just by clicking properties I can see that the avis that do play with no problem are XVID MPEG-4.  The one that is not playing nicely is DivX MPEG-4 Version 5.  I have begun converting to mp4 using Handbrake.  Is this a waste of my time?
That should work assuming you're encoding to a format compatible with your player.

---

### Post by alphacrucis2 on 2011-12-04
> **ubunwhat said:**
> Again, pardon my ignorance.  Medianinfo?  I don't see that in the repository.  And I don't see Vic either.  Can you explain that a bit for me, please?

Maybe this ppa for mediainfo:

[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

The other package is v**l**c (= [videolan]("http://www.videolan.org/vlc/")) rather than v**i**c. Vlc is in the ubuntu universe repo.

---

### Post by ubunwhat on 2011-12-04
Again my video ignorance is showing.  I started converting without checking.  I just looked and it is using H.264 whatever that is.  Criminey, I just wanted to watch a few movies.  This is way more involved than I thought,lol.

---

### Post by MoreOrLess on 2011-12-04
That should work assuming you're encoding to a format compatible with your player.
[http://community.insigniaproducts.com/t5/Blu-ray-and-DVD-Players/NS-WBRDVD2-Does-it-support-DivX-XviD-with-firmware-updates/m-p/37887/highlight/true#M7288](http://community.insigniaproducts.com/t5/Blu-ray-and-DVD-Players/NS-WBRDVD2-Does-it-support-DivX-XviD-with-firmware-updates/m-p/37887/highlight/true#M7288)

Divx looks to be unsupported, even with newest firmware.

---

### Post by alphacrucis2 on 2011-12-04
> **ubunwhat said:**
> Again my video ignorance is showing.  I started converting without checking.  I just looked and it is using H.264 whatever that is.  Criminey, I just wanted to watch a few movies.  This is way more involved than I thought,lol.

[H.264]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC") is a particular codec. Not much use if your player doesn't understand it. You want to convert to a codec that your player does understand. I don't use handbrake but I'm sure that it would allow you to select XVID as the output codec. If not then you can do it from the command line using ffmpeg or try another GUI program such as avidemux.

---

### Post by internetprofiles1 on 2011-12-04
avidemux can convert it to Xvid 4 or what ever version u require. My plaver is divx compatible only and some avi files coded in xvid do not play. avidemux does the job in about 30mins depending on settings chosen.

---

