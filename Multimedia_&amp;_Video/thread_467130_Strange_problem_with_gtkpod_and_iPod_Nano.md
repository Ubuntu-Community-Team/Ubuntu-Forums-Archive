---
title: "Strange problem with gtkpod and iPod Nano"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by PacShady on 2007-06-07
Hey all

I just bought myself a new iPod Nano, and figured I'd give gtkpod a go for transferring music. All seemed to go well, except I noticed a strange error that occurred with the iPod while playing - periodically, it would spontaneously reset itself at the beginning of random songs.

I thought that maybe I got a dodgy iPod. After all, it definitely wouldn't be the first time I bought something brand new and it didn't work. But, I figured I'd load up a copy of Windows and try using iTunes to transfer the same music. So far, I haven't noticed a problem, it seems to be working 100%.

So has anyone else ever experienced this strange problem when using gtkpod on your iPod? I figured it might be the slightly different way gtkpod handles files on the iPod compared to iTunes. Any ideas on how to fix it, WITHOUT installing iPodLinux? (it's brand new, if I install that it might void the warranty! LOL)

'Shady

---

### Post by rfurman24 on 2007-06-07
I have noticed this with my nano but not my old ipod. I just took the certain songs off. The nano seems buggy to me anyway.

---

### Post by PacShady on 2007-06-10
I thought I had luck using Amarok instead, but after a day or so it had the same problem after I added more songs.

I'm gonna try using JUST iTunes, if that doesn't fix it then I'll take it back and get a new one.

'Shady

---

### Post by PacShady on 2007-06-22
Yup, iTunes works fine with the 2G Nano.

Seems there's something with how Amarok and gtkpod and such transfer files to the iPod. The file names are something like kpod12312987.mp3 when using these programs, but using iTunes they're more like AHSYJS.mp3.

I'd hazard a guess that ITunes.db is written slightly differently too. This seems to mean that Linux programs (and possibly Windows alternative programs) aren't able to write to the iPod the way it wants them to.

I don't like this. Apple has just struck a blow against the Open Source community. Maybe Microsoft bought them out...

'Shady

---

### Post by DanielBeaver on 2007-06-25
I'm having this same problem with my 2G nano. For the last 6 months I had been using iTunes with no problem, but now that I'm using amarok my ipod crashes when playing certain songs.

I removed a bunch of the songs that were crashing, thinking that there was some funny problem with the way they were encoded. Didn't work too well - now *other* songs crash the ipod, songs that did not previously crash it. Several songs will crash the ipod midway through the song.

I did try upgrading the firmware through iTunes (which wipes the ipod in the process), but to no avail.

This is really annoying - to the point that I'm considering just using iTunes instead of amarok to manage my music.

---

