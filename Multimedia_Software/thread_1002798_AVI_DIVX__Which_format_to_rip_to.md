---
title: "AVI DIVX ?? Which format to rip to"
date: 2008-12-05
forum: Multimedia Software
---

### Post by drfox on 2008-12-05
I want to back up my collection of DVDs.
Which format should I rip to? AVI, DIVX, something else?
Advantages, disadvantages of one over another?
Thanks.

---

### Post by fowie on 2008-12-05
AVI actually isn't a format, it's a container.  You can rip DIVX format and put it inside an AVI container.  I find that DIVX looks pretty good, but if you're in linux there's more support for XVID (open source DIVX).  I typically rip mine as XVID and copy the audio straight in (keeps 5.1, Dolby, etc...) and store it in an AVI container (so my files are XVID videos but the extension is .avi).  MythTV, XBMC, and VLC all play them just fine.  I've also done Ogg, and didn't notice much difference except that Ogg seemed to compress the files a little more but the number of players that could read them was fewer.

---

### Post by drfox on 2008-12-08
Very clear. Thank you, Fowie!

---

### Post by ClarkePeters on 2008-12-19
drFox may not be checking back here, as this is a couple of weeks old, but for anyone else, I use Thoggen to save my video backups, it's quick, simple, saves small files, and can playback in VLC or Totem Movie Player (the standard install with Ubuntu). 

You only need to check the Main Title >>> continue >>> choose your file size (how large or small would you like your resultant file to be), and that's it.  It takes a long long time (maybe 10 hours or so for a two hour video), so I do mine overnight.

Later, you can burn them by using vlc, avidmux (or ffmpeg, mencoder, transcoder or other choices) to convert the .ogv file to an avi or something else for burning. The file converts back a little oversized for a two hour dvd (4.7 gb), so you may have to play around with bitrate or something to keep your file size down.

---

### Post by binbash on 2008-12-19
avi is a container, you can rip your dvds via dvd:rip or k9copy

---

