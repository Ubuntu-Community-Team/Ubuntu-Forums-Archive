---
title: "FLV or AVI to Playable DVD"
date: 2010-02-24
forum: Multimedia Software
---

### Post by HomoGleek on 2010-02-24
Hi, 

I'm looking for some help on how to burn FLV or AVI to Playable DVD? Anybody help?

---

### Post by KeLa on 2010-02-26
Hi,

Just finished one test about subject.
What i done about is as follows.
First converted flv to avi with mencoder
```
mencoder ./infile.flv -ovc lavc -oac mp3lame -o output.avi
```
then converted avi to dvd with avidemux
(found old instructions from [http://forum.videohelp.com/threads/185976-LINUX-AVI-to-DVD-Encoding-and-Authoring-BASIC](http://forum.videohelp.com/threads/185976-LINUX-AVI-to-DVD-Encoding-and-Authoring-BASIC)) skipped all steps after avidemux
and burned generated mpg file to dvd with Brasebo.
And currently watching it with sony blueray player.

ps. what ever you can play with sony player you can play with any other player and
that's from my own experience from past when sony introduced first dvd player that can play home made cd audio discs. Only maxell rw media was success in that (tested many different media before found right one not any media made for audio data was successfull).
My Technics cd player played what ever you try to feed it (even round bread if it contained music and fit in the player) and that player is from time before cd-r/cd-rw drives for pc computers.

---

