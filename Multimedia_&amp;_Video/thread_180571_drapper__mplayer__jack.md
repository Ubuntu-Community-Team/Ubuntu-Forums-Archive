---
title: "drapper / mplayer / jack ?"
date: 2006-05-22
forum: Multimedia &amp; Video
---

### Post by stbub on 2006-05-22
Anyone got mplayer to work with jack in Drapper?

---

### Post by dolson on 2006-05-23
I coulda swore I read that Mplayer was dropping JACK support.. But I don't remember where I heard that. A dream perhaps?

Either way, it's Dapper. ;)

---

### Post by stbub on 2006-05-24
Sorry about the typo :-)

It sux if mplayer is dropping jack.

What's a good audio player that works with jack? (xmms sux a lot of cpu)

---

### Post by bwanab on 2006-05-24
The only jack player that I know of is Alsaplayer. The user interface kinda blows, but the sound quality is the best that I've found on any of the players on my dapper system.

---

### Post by stbub on 2006-05-24
[QUOTE=bwanab]The only jack player that I know of is Alsaplayer. The user interface kinda blows, but the sound quality is the best that I've found on any of the players on my dapper system.[/QUOTE]

I tried it.  the GUI is so-so, but more importantly, I haven't found a way to hook it up to a specific jack port from the command line (mind you I haven't tried hard.  I'll probably have to look at the source code).  I want to hook it up to a hardware track.

---

### Post by RFScheer on 2006-06-20
I have set up both alsaplayer and xmms with the xmms-jack plugin and they both work very well with jack for music files.  xmms works well for various types of internet radio.

BruteFIR is an important part of my sound system and it works well inside jack also.  

I'm running both xmms and brutefir on realtime settings.

The problem is Mplayer.  The standard dapper package appears to not include the jack driver for some reason.  I'm trying to set up dvd playback with brutefir filtering so I need it to work through jack.

I guess it's time to look at compiling mplayer from cvs or svn.

---

