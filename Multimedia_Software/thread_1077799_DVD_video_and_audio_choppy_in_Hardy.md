---
title: "DVD video and audio choppy in Hardy"
date: 2009-02-22
forum: Multimedia Software
---

### Post by nrKist on 2009-02-22
Basic laptop specs...
# Intel Celeron M 1.5 GHz Processor (1MB L2 Cache, 400MHz Front Side Bus)
# 1024MB DDR2-533 PC4200 RAM 
# ATI Radeon Xpress 200M Motherboard Chipset
# ATI Radeon Xpress 200M Graphics (32MB-128MB Dynamically Shared Memory)
# Toshiba 60GB 5400rpm (MK-6026GAX) Hard Disk
# CD-RW/DVD-ROM Combination Drive (CD-ROM Read 24x, DVD-ROM Read 8x, CD-R Write 24x, CD-RW Write 24x)

I'll preface this with the fact that I dual boot Feisty and Hardy. In Feisty the DVD playback is, and has always been, flawless.

In Hardy the image and sound jerk as though the drive can not supply data quickly enough. This may be the case because my other observation is that when I stop the video and restart it, it plays smoothly up until the point I had stopped it since it doesn't have to access it from the drive. As soon as the drive begins accessing data again the image and sound become choppy again. 

It does not matter which front end or back end I use, the result is always the same.

Suggestions? Perhaps some sort of software cache setting for the drive that I need to increase?

Thanks.

---

### Post by nrKist on 2009-02-23
Bump

Things do disappear quickly from the front page, but I'd still appreciate some help if anyone has a suggestion.

---

### Post by mocha on 2009-02-23
It's hard to figure out what the problem is.  The only thing I can suggest is setting your DVD player's speed, to prevent the spin up and spin down. I have to do this sometimes with MP3 CDs, the drive wants to race up to 52x and buffer all the music, but then the buffer runs out and the music stalls while the drive spins up again.  Try this:

```
eject -x2
```

That will put the player in 2x read mode, should be fine for a video DVD.

---

### Post by nrKist on 2009-02-26
Thanks for the reply Mocha. Sadly that didn't have any effect. I see what you are saying about the spin up and down but that isn't happening here. The drive is spinning constantly. Perhaps there is just too much going on in the background. I'm not running any other programs when I'm trying to watch a DVD, but there are an awful lot of background processes going on. Perhaps if I could pare those down to a minimum. I wonder how many of them are really necessary.


Strange that it would work so well in Feisty and so poorly in Hardy. After enjoying Feisty  so much I was hoping to go with one of the LTS releases. Perhaps I'll just have to try compiling my own apps and keep using Feisty.

---

