---
title: "Watch an *.avi on Ubuntu?  Make it into a DVD?"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2006-11-14
I am using Ubuntu 6.10.  I used automatix to get various multimedia supplements when I installed my system as Breezy Badger.

I downloaded an avi I want to watch.

When I click on it, totem comes up and tells me I need a new plugin to watch the file.  Where can I get such a plugin?

I would like to burn this avi to a dvd that a friend can watch on her television and that I can watch on my computer.  Is there software to convert this to such a format?  What format would I want to use?

Thanks in advance for any information.

---

### Post by taurus on 2006-11-14
I recommend you use mplayer to play on your computer and if you want to convert it DVD so you can watch it a DVD player, then use DeVeDe...

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by fakie_flip on 2006-11-16
Which one is better? tovid or Devede? Have you tried tovid?

---

### Post by taurus on 2006-11-16
> **fakie_flip said:**
> Which one is better? tovid or Devede? Have you tried tovid?
Yes, I have tried tovid.  They're both equally as good although devede is much faster...  It takes less than an hour for devede while tovid can take up to 4 hours!

It doesn't hurt to try out both and decide which one you want to keep.

---

### Post by fakie_flip on 2006-11-16
> **tinker123 said:**
> I am using Ubuntu 6.10.  I used automatix to get various multimedia supplements when I installed my system as Breezy Badger.

I downloaded an avi I want to watch.

When I click on it, totem comes up and tells me I need a new plugin to watch the file.  Where can I get such a plugin?

It is recommended to use MPlayer and it supports many formats. If you must use totem, then install the package totem-xine. Read here.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

> I would like to burn this avi to a dvd that a friend can watch on her television and that I can watch on my computer.  Is there software to convert this to such a format?  What format would I want to use?

If you have svideo out on your video card and svideo on your tv, then you can connect them and watch video playing on your computer and showing on your tv.

---

### Post by fakie_flip on 2006-12-30
> **taurus said:**
> Yes, I have tried tovid.  They're both equally as good although devede is much faster...  It takes less than an hour for devede while tovid can take up to 4 hours!

It doesn't hurt to try out both and decide which one you want to keep.

From what I read, DeVede is not that good at all. People's audio gets screwed up everytime. It is bad enough to make most of them switch programs. If I could find a rpm for Fedora Core 6, I would try it on the FC computer and ToVid.

---

### Post by 3rdalbum on 2006-12-30
> **fakie_flip said:**
> From what I read, DeVede is not that good at all. People's audio gets screwed up everytime.

That's an audio/video sync problem with MEncoder, which is DeVeDe's backend. DeVeDe has a special control which delays or advances the audio by a specifyable amount, to compensate.

---

### Post by binks on 2006-12-30
if its just one avi per dvd then use the tovid wizard i made in my signature and if its time of encode that is of importance then i can add the -ffmpeg flag to the script to make the process faster 
just my 2 peneth
binks

---

### Post by crispy_420 on 2006-12-30
If these videos are a standard DivX/Xvid file, look into getting a home player that works with them. I got a Philips home player that plays them just fine. Just pop in the disc and it starts.

Another option is an embedded linux media player. I got one from Galaxy (in the US, MacPower in the rest of the world) and it has to be the coolest gadget for carry movies on the go.

[Galaxy 3500 TVisto]("http://www.galaxymetalgear.com/Products/3500tvisto.html")

It will play almost anything. You just add your own hard drive. So for less than $200 (if you buy a hard drive) you can carry hundreds of full length (700MB) movies with you. It even plays iso images. The only downside is hard drive format support. To be stable in linux you'll have to use fat32, but then no DVD iso's. 

These are just my easy ways out. Just so I don't have to wait to render an entire DVD.

---

