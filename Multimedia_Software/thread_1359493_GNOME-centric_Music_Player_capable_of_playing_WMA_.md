---
title: "GNOME-centric Music Player capable of playing WMA Lossless"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Aiello on 2009-12-19
I'm looking for a GNOME music player that can handle WMA lossless files. Basically, any GNOME-friendly music player that uses Xine as its backend (Xine can handle WMA lossless but Gstreamer can not, for whatever reason) would work. 

Right now I'm using GNOME Mplayer to play my music, but as it is meant to be a video player, it isn't exactly the best way to manage my music! I'd rather not use Amarok or other KDE-based player, as I don't want to download a bunch of KDE dependencies just to play music! 

Any suggestions?

-Thanks!

---

### Post by RedSingularity on 2009-12-19
How about VLC player?  Thats built for video and audio files.

---

### Post by Aiello on 2009-12-20
Unfortunatly, it appears that VLC can't hande WMA lossless either.

---

### Post by Yellow Pasque on 2009-12-20
Install dir2ogg and use that script to convert your wma lossless to .ogg

---

### Post by typos1 on 2010-01-22
How would he do that as wma lossless isnt recognised by anything on ubuntu?-You just get error messages...

---

### Post by mc4man on 2010-01-22
in a 32 bit install with w32codecs installed mplayer (inc. frontends) and a xine engine player can decode wmal (totem-xine, amarok, ect.

(A vlc that's built with with dmo loader enabled can also decode wmal, though you'd need to build that yourself

---

### Post by typos1 on 2010-01-22
Well I ve installed movie with the xine backend and it still wont play em! Says it needs a plugin, searches then cant find any. Same as without the xine backend

---

### Post by mc4man on 2010-01-22
> Well I ve installed movie with the xine backend and it still wont play em!

Well as mentioned you need to install w32codecs, obviously for 32bit ubuntu installs only

Either[ add medibuntu ]("https://help.ubuntu.com/community/Medibuntu")to sources and then 
```
sudo apt-get install w32codecs
```

or go here and directly dl and install

[jaunty]("http://packages.medibuntu.org/jaunty/w32codecs.html")
[karmic]("http://packages.medibuntu.org/karmic/w32codecs.html")
[lucid]("http://packages.medibuntu.org/lucid/w32codecs.html")

Edit: not sure if on jaunty (use karmic, lucid) if libxine1-ffmpeg is installed with totem-xine, amarok ect. If not you need that also (and not just for wma

---

### Post by typos1 on 2010-01-23
Using Karmic(64bit)-hadnt changed it on profile sorry-I ve installed movieplayer with xine and libxine1-ffmpeg is also installed. Will installing w32 codecs remove the 63 bit ones?

---

### Post by cascade9 on 2010-01-23
Stupid WMA 'lossless' files. Next time, use a real lossless format (.flac, .wv).

---

### Post by Yellow Pasque on 2010-01-23
> **typos1 said:**
> Using Karmic(64bit)-hadnt changed it on profile sorry-I ve installed movieplayer with xine and libxine1-ffmpeg is also installed. Will installing w32 codecs remove the 63 bit ones?

No, but you need a 32-bit player to use them..

---

### Post by typos1 on 2010-01-23
Right, ok thanks. Think I ll just turn them into .wavs again in windows and go from there.

> **cascade9 said:**
> Stupid WMA 'lossless' files. Next time, use a real lossless format (.flac, .wv).
  
I used to store all music as wma lossless files before I started using ubuntu. 

Most cd players (or at least the ones I owned-hi fi, car etc) can play em. 

Sound wise theyre fine.

I will be using flac or something else in future. I m no Windows fan, but the problem here is really lack of support for them NOT theyre existance, or lack of quality and they are "real" lossless files...

---

### Post by cascade9 on 2010-01-23
AFAIK, WMA lossless support comes with WMA general support. So all the stuff out there that plays .WMA should play the lossless version. 

> **typos1 said:**
> I will be using flac or something else in future. I m no Windows fan, but the problem here is really lack of support for them NOT theyre existance, or lack of quality and they are "real" lossless files...

Catch 22? 

If people dont use flac, then no-one builds hardware that supports it, so no-one uses it, so no-one builds the hardware, etc etc. 

My portable media player supports .flac (and .ogg vorbis as well). It sucks to try to find a car media player with .flac support, but there are quite a few home media solutions that support .flac. 

BTW, I'm 99% sure I've seen a bit of debate about if they6 are lossless or not at hydrogenaudio, places like that. I avoid them more because I dont want to add to the microsoft juggernaut. Besides that, I always removed WMP from windows so it would have been a right pain to even figure out how to rip them....

---

### Post by typos1 on 2010-08-23
Just re-read this-Dension do products that support .ogg files and you can use flac as a codec for ogg, then you d have a car player that can play flac!

---

