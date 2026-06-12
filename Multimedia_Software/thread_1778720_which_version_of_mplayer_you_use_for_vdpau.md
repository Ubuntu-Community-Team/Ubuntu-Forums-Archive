---
title: "which version of mplayer you use for vdpau"
date: 2011-06-09
forum: Multimedia Software
---

### Post by beew on 2011-06-09
I use mplayer from  this ppa [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc") It works flawlessly with vdpau (and works well without vdpau as well, it uses ffmpeg-mt, no need for the coreavc stuffs). 

I am very happy with it but out of curiosity I am testing other versions on my Natty test install. Many people recommend the MOTU ppa for mplayer so I tried it out and it seems that vdpau doesn't work at all (with gnome-mplayer and Umplayer) With this version gnome-mplayer and Umplayer stutter and crash for some high definition clip with cpu usage at 100%, but with ripps' version the playback is smooth with cpu usage around 10%.

Since ripps' ppa is not that well known apparently (most people would recommend MOTU for some reasons) I am wondering what version of mplayer do people use to take advantage of vdpau? (Of course you can compile it yourself )

Aside: I use MOTU's ffmpeg ppa on another Natty test install and apparently it doesn't work witth libvacodec52-extra. Is it true that softwares in the MOTU ppa, while newer than the Ubuntu version, is still crippled?

---

### Post by beew on 2011-06-10
So no one uses mplayer with vdpau?

---

### Post by beew on 2011-06-17
Ok, just figured it out. Ripps version is actually mplayer2, that's why it works so much better than MOTU and the other builds I have tried.

[http://ubuntuforums.org/showthread.php?t=1034075&page=48](http://ubuntuforums.org/showthread.php?t=1034075&page=48)

---

### Post by Perfect Storm on 2011-06-25
I have the latest mplayer (via PPA) installed and using Gnome Mplayer (v1.04b - compiled) and I don't have any problems vdpau.

---

### Post by SeijiSensei on 2011-06-25
I build mplayer2 from scratch; it uses VDPAU.  I've also compiled mplayer from source with equal success with respect to VDPAU.  mplayer2 has better support for subtitles as it uses a more recent libass version.  It also supports ordered chapters in Matroska containers.

---

