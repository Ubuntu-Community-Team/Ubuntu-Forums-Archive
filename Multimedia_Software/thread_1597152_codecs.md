---
title: "codecs"
date: 2010-10-15
forum: Multimedia Software
---

### Post by aaira on 2010-10-15
new to linux. Just installed it on my laptop.

Videos are appearing grainy (like boxes)-no sharp images.

Should I be considering some video codecs?
I am using VLC Player and PS3 Media Server (dlna server)

---

### Post by macem29 on 2010-10-15
I'd look at video driver as a culprit before messing with codecs, VLC is a very complete player on a system with video properly working

---

### Post by Megaptera on 2010-10-15
Hi,
Useful guide  here if it's not your drivers.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope that helps?

---

### Post by endotherm on 2010-10-15
well, in my opinion VLC, while being able to play anything, is generally grainy and has color compression issues, so I usually use [smplayer ]("https://launchpad.net/%7Ervm/+archive/smplayer")or totem with the [ubuntu restricted extras]("https://help.ubuntu.com/community/RestrictedFormats") (codecs) and the [mediubuntu ]("https://help.ubuntu.com/community/Medibuntu")repos.
 
vlc does not use external codecs, so there isn't anything to download that will improve the situation if indeed codecs are the issue. you may be able to get a much better picture by tweaking the settings but that's about all the control you get with it. 

I would start by looking at your vid card driver. what kind of card do you have and have you installed a restricted driver for it?

do the same videos look grainy in other players, like totem? 

what res is the video at and what format is it in? is it 720 or higher?

---

