---
title: "WMA Files"
date: 2009-03-27
forum: Multimedia Software
---

### Post by deanhopkins on 2009-03-27
Hey, been a while since ive been here.. just upgraded to 8.10 - and i cant get my WMA files to play. They used to play fine on my old os - i got a new system and upgraded to 8.10 at the same time, and now they wont play.

Ive tried banshee, Amarok and Songbird (This is preffered) and none of them play.

IIRC, I used automatix to install codecs before - however the website is now down.

Any ideas? Thanks guys.

BTW: Its about 10 mixtapes that are WMA, and they are pretty high quality so converting them isnt an option :(

---

### Post by mc4man on 2009-03-27
get w32codecs from here
[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

For amarok add libxine1-ffmpeg

Amarok will play all the normally available wma (wma2, wmap, wma lossless
your other 2  players will have some limitations

---

### Post by balaknair on 2009-03-27
Open a terminal, type in ***sudo apt-get install ubuntu-restricted-extras*** to install the codecs(as well as non-open source/restricted stuff like Adobe Flash Player, Sun Java and MS TrueType Fonts and DVD, MP3, Quicktime playback).

---

### Post by deanhopkins on 2009-03-27
Thanks guys. 

BTW, is automatix still about? The website seems to be down and all the posts i see about it on the search are from like '06.

To be honest - I swapped to FedoraCore for a while, and have only recently come back to ubuntu - what a fool ive been.

8.10 is the simplest thing to install (Easier than windows..hell yes). If linux is to go forward, it will be through ubuntu. Its so much better for general use than the others ive tried - and the community support makes it that way.

---

### Post by logos34 on 2009-03-27
> **deanhopkins said:**
> Thanks guys. 

BTW, is automatix still about? The website seems to be down and all the posts i see about it on the search are from like '06.

It's been discontinued.

[http://en.wikipedia.org/wiki/Automatix_(software](http://en.wikipedia.org/wiki/Automatix_(software))

My own very humble opinion is that the criticism from the ubuntu core dev team was overblown, because so many people used it without incident (myself included).  Maybe it didn't meet specs, and had potentially serious security issues, but it seemed to me that it brought in a lot of noobs from the windows world who would have given up on ubuntu installation and configuration on the first day were it not for the fact that Automatix2 effectively automated the process of getting all the multimedia codecs and whatnot.

---

