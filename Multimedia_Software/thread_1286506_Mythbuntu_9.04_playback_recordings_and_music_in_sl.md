---
title: "Mythbuntu 9.04 playback recordings and music in slow motion"
date: 2009-10-09
forum: Multimedia Software
---

### Post by LoermansA on 2009-10-09
Hi all,

I have a weird problem. I have a combined MythTV front end and back end and this has always served me well. Equiped with a Hauppauge PVR 500 dual tuner card, it serves all my recording and playing of media needs. Problem is, out of the blue (no updates done) it started to playback recordings and mp3 music in slow motion. I cannot get it to play them back in normal speed. I've tried all the keys and menu options, but it insists on playing it back in slooooowwwww mooooottioon. This has always worked perfectly, until now.

I have now updated it with all the latest updates as of this morning (rocktober 9th) and the problem remains. Playing back media stored on a server in mplayer gives me no problem.

Any ideas? If all else fails I'm going to do a reinstall, but I wanted to wait with that until MythKoala came along.

Regards,

Arjan

---

### Post by LoermansA on 2009-10-14
I solved the problem by reverting back to Alsa (according to [this]("http://ubuntuforums.org/showpost.php?p=5539687&postcount=331") procedure. I'd switched to OSS4 because that seems to work better with a Snes9x. So if anybody else has this problem, check to see if you're running OSS.

Arjan

---

