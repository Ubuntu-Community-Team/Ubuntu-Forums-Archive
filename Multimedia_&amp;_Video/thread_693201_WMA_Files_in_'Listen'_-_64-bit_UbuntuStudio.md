---
title: "WMA Files in 'Listen' - 64-bit UbuntuStudio"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by otheracco on 2008-02-10
I'm a recent convert, and I'm not going back.  Ubuntu is much nicer than Vista 64-bit and has phenomenal performance.

Anyway, I like 'Listen' a lot and would like to use it for my music collection (which is all in wma lossless).  

I've read through some of the posts already, but nothing has helped yet (I've spent hours so far).

I'm extremely pleased with the sound quality with wma lossless and don't want to convert to another standard, but I'd like to ask this question anyway.

Does anyone know if converting from WMA lossless to FLAC will degrade the file at all (will it compress it further)?  The thing is, is that I'm unsure if doing conversions from an already converted lossless format to another will step down the quality.  It just seems like an ugly solution to my problem.

That isn't my real question though, what I'm really asking is "Can anyone help me set 'Listen' up for WMA playback on my 64-bit UbuntuStudio install?

I've been toying around with different distros and am sticking with Ubuntu since it's so complete.  It's much more 'together' than any other low-latency kernel distro I looked at.

---

### Post by MetalMusicAddict on 2008-02-11
> **otheracco said:**
> Does anyone know if converting from WMA lossless to FLAC will degrade the file at all (will it compress it further)?

No. Lossless is lossless. Though I haven't seen a way to go from WMA lossless to FLAC on Linux. 

> That isn't my real question though, what I'm really asking is "Can anyone help me set 'Listen' up for WMA playback on my 64-bit UbuntuStudio install?

Install the gstreamer codecs via Synaptic. They have -bad and -ugly after them. I dont even know if you can play WMA lossless back on linux.

---

### Post by balbinny on 2008-04-04
This worked for me: [http://www.listen-project.org/ticket/722](http://www.listen-project.org/ticket/722)
Rpelace song.py .....gksudo gedit /usr/lib/listen/song.py
with the newer version then restart.

---

