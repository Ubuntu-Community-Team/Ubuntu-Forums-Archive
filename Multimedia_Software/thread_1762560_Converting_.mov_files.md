---
title: "Converting .mov files"
date: 2011-05-19
forum: Multimedia Software
---

### Post by Muzramp on 2011-05-19
Hey guys, I'm new to the forums here. I've been using Ubuntu for a while now and I love it. I just can't find a program to convert my .mov files to any video format that works good in Linux. I tried Winff/Transmageddon/Avidex/and one that starts with "A" I can't remember the name. Anyone know any other programs? :)

---

### Post by coffeecat on 2011-05-19
Welcome to the forum

Firstly, you should be able to play .mov files just fine in Ubuntu. Install the package ubuntu-restricted-extras for most of the codecs you will need. If you can't play .mov files at the moment, it may be because you don't have the right codecs installed. The restricted extras package will also give you flash, java and microsoft core fonts which you need for some webpages to render properly and for serious word-processing.

Next - the package beginning with A could be Avidemux, but I'm not too keen on it. It has a habit of losing audio/video sync.

If you want to convert .mov files to Xvid AVIs you could do a lot worse than install devede from the repositories. It's really a DVD authoring tool, but when you first open it, the last choice is "DivX/MPEG-4". This will convert many video formats to AVI. Simple and reliable.

There's also the non-repository [Transcoder]("http://transcoder84.sourceforge.net/"). You have to download the .deb file and install it yourself, but you get a sniffy "this package is not of good quality" or words to that effect from Software Centre. Works for me though.

---

