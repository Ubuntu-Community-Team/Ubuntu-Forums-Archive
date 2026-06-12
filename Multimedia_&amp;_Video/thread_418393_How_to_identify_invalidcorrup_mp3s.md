---
title: "How to identify invalid/corrup mp3s??"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by stevanbt on 2007-04-22
Hi all,
I have a collection of MP3s that I've built up to over the years, somewhere in that time I've got some invalid or corrup mp3s - i.e. when I try to play them they won't play.  This isn't too much of a problem as I just don't bother trying to play them.  

However, I have installed MythTV and when it tries to scan my MP3 library I think it's getting stuck when it finds an invalid mp3.  So my question is - how can I identify (and delete) invalid mp3s via a script, or batch, file.  I had thought that it may be possible to try to re-encode my collection and reject anything invalid, but I don't want to end up with mp3s that are lower in quality than the ones I started with.  It isn't an option to play/delete them manually.

Thanks in advance, Steve.

---

### Post by tgalati4 on 2007-04-22
in a terminal:

sudo apt-get install easytag

Run your collection through easytag.  It will highlight malformed ID3 tags that are probably tripping up the database for MythTV.

---

### Post by reclusivemonkey on 2007-04-23
> **stevanbt said:**
> Hi all,
I have a collection of MP3s that I've built up to over the years, somewhere in that time I've got some invalid or corrup mp3s - i.e. when I try to play them they won't play.  This isn't too much of a problem as I just don't bother trying to play them.  

However, I have installed MythTV and when it tries to scan my MP3 library I think it's getting stuck when it finds an invalid mp3.  So my question is - how can I identify (and delete) invalid mp3s via a script, or batch, file.  I had thought that it may be possible to try to re-encode my collection and reject anything invalid, but I don't want to end up with mp3s that are lower in quality than the ones I started with.  It isn't an option to play/delete them manually.

Thanks in advance, Steve.

I was looking for an application in synaptic yesterday and spotted a program which does exactly this; searches through mp3s and looks for corruption. I'm afraid I don't recall the name, but you should be able to find it. It was a CLI application, hope that doesn't put you off.

---

