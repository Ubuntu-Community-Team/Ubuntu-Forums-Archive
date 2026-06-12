---
title: "[SOLVED] Video Conversions"
date: 2008-12-16
forum: Multimedia Software
---

### Post by icyest on 2008-12-16
I'm kind of stick of going around trying to find a suitable video format converter for linux. What Online video conversion sites can you think of? Can you name name good high quality ones, not cheep desolate ad-filled sites.

---

### Post by Xzoky on 2008-12-16
I don't know any, but I think you definitely should give [Avidemux]("http://en.wikipedia.org/wiki/Avidemux") a try. It's in the repos.

---

### Post by prshah on 2008-12-16
> **icyest said:**
> I'm going around trying to find a suitable video format converter for linux.

I advise ffmpeg; very simple and fast to use. It's in the repos, and you can install by [clicking here]("apt://ffmpeg").

While it will handle practically anything you throw at it, I'd recommend you download the source and compile it; it's simple, easy and adds support for (?) h.264 (?) video codec.

Usage is as simple as```
ffmpeg -i infile.avi outfile.mpg
``` or .mp4 or whatever you like.

---

### Post by icyest on 2008-12-17
> **prshah said:**
> I advise ffmpeg; very simple and fast to use. It's in the repos, and you can install by [clicking here]("apt://ffmpeg").

While it will handle practically anything you throw at it, I'd recommend you download the source and compile it; it's simple, easy and adds support for (?) h.264 (?) video codec.

Usage is as simple as```
ffmpeg -i infile.avi outfile.mpg
``` or .mp4 or whatever you like.

I don't quite understand. I clicked on the link up there,  and something installed in my computer. Now what? My Applications doesn't reveal any newly installed programs like Windows would. This is so confusing!

---

### Post by wolfen69 on 2008-12-17
it won't show up in your applications. just put the file you want to convert into your home folder and run the command shown. just replace infile with the name of the file you wish to convert. and of course replace .avi with whatever it is. if you want a gui frontend for ffmpeg, (what you just installed) download [winff]("http://code.google.com/p/winff/"). easy. winff will show up in applications.

---

