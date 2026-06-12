---
title: "How to clear Video cache"
date: 2010-08-22
forum: Multimedia Software
---

### Post by jonnan on 2010-08-22
Ubuntu 10.4 64-bit

First, I am almost certainly using the wrong term here, but if I knew for sure what I was looking for I probably would have managed to google it.

In a fit of minor insanity, I used ffmpeg to convert all my video files I've impulse downloaded over the last decade or so to mp4, mostly because Easytag will happily tag them an assist in reorganizing them, but of course some videos didn't convert, either properly or at all due to issues with the original file so I'm going through and killing the original when it worked and sorting them into another directly when it didn't, More fun than mortal man was meant to know.

But - every 108 -123  (Going by the filecount in my trash when it happens; I've wondered if the actual number is 127 or 128 but haven't gotten that definitive yet.) videos or so, totem dies, and so does every other video player I can use, VLC, mplayer, et al. 

For awhile I rebooted, then I figured out just logging out/in cleared the error, but I've yet to narrow down what exactly is causing it.
Since it crosses all players I can only assume that there is some kind of cache that is getting filled up that is cleared when you logout, but after doing some digging it's nothing cleared by anything I've found like bitbleach.

As bugs go, it's far more an annoyance than anything critical, but, it *is* an annoyance.

Any thought would be appreciated.

Jonnan

---

### Post by no2498 on 2010-08-22
in/on 910 and up they say you need to restart the computer
to clear the cache

you can see if this helps some click places clear recent documents

---

### Post by kotnik on 2010-08-22
Sounds freaky, but here's what you could do, to get some info. Next time all players decide to give up on you, fire up terminal, and start troublesome video with mplayer and give us here the output it makes.

---

### Post by kotnik on 2010-08-22
> **no2498 said:**
> in/on 910 and up they say you need to restart the computer
to clear the cache

OP thinks that there's some caching going behind his back, but I doubt it. Restarting computer is a bit extreme.

---

### Post by jonnan on 2010-08-22
Well, I figured out how to restart the x-server (sudo /etc/init.d/gdm restart), which works without my logging out and narrows it down to something in the X-server caching. 

Still wish I could figure out the root cause, but given that I have yet to understand how codecs work it's probably as far as I'm going to get on this unless someone smarter than me figures it out.

Jonnan

---

### Post by jonnan on 2010-08-22
Okay, just to make an odd problem odder - restarting x-server worked fine the first few times - then started killing pulseaudio somehow?

Would have audio in the login screen, but not at the desktop. After a bit of creative panic I figured out it would fix itself if I deleted the .pulse folder and rebooted (just logging out doesn't work), but everytime since then that I've restarted the x server it has done this. wtf, over?

Had not seen the prior posts, but yes I will try getting a log from mplayer or totem from the commandline.

Jonnan

---

### Post by kotnik on 2010-08-23
> **jonnan said:**
> Had not seen the prior posts, but yes I will try getting a log from mplayer or totem from the commandline.

It might shed some new light on the problem.

---

