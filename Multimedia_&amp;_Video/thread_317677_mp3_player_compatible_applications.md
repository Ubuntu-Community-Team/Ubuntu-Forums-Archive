---
title: "mp3 player compatible applications"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by kcy29581 on 2006-12-12
Hi all,

I'm confused about how to use mp3 players in Ubuntu; specifically I have a Samsung YP-Z5.

When I plug it in the pc, Rhythmbox detects it flawlessly and I can see it in the sources list.

I'm trying out a few other music players, such as:
 - Listen
 - Exaile,
but I can't seem to get the mp3 player to work here (maybe it's not a feature?)

Does anyone know of other applications that can play mp3 players in Linux other than Rhythmbox?

Thanks

---

### Post by Paul41 on 2006-12-12
Banshee will play mp3's.

Have you installed the packages for restricted formats yet? You will need this to be able to play mp3's.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by kcy29581 on 2006-12-13
> **Paul41 said:**
> Banshee will play mp3's.

Have you installed the packages for restricted formats yet? You will need this to be able to play mp3's.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I'm not talking about "playing mp3's". I'm asking if you know any media players that use **hardware mp3 players. such as the Samsung YP-Z5.**

Example: I plug in the Samsung YP-Z5 in my PC via a USB cable. Result: I can actually "see it" in Rhythmbox as a source. No fiddling necessary.

Are there any other Linux media players that do this? All I keep seeing is "iPod support". Not everyone has just an iPod...

---

### Post by cborga1985 on 2006-12-13
> **kcy29581 said:**
> I'm not talking about "playing mp3's". I'm asking if you know any media players that use **hardware mp3 players. such as the Samsung YP-Z5.**

Example: I plug in the Samsung YP-Z5 in my PC via a USB cable. Result: I can actually "see it" in Rhythmbox as a source. No fiddling necessary.

Are there any other Linux media players that do this? All I keep seeing is "iPod support". Not everyone has just an iPod...
did you try amarok? exaile only has ipod support right now. i know the feeling btw because i have a [phillps gogear hdd6330]("http://reviews.cnet.com/Philips_GoGear_HDD6330_Jukebox_30GB/4505-6490_7-31503513.html") and i haven't found any support for it at all.

---

### Post by kcy29581 on 2006-12-13
I haven't tried amaroK, as I was looking for GTK apps (no particular reason though, if amaroK works and it's better, then so be it!)

---

### Post by cborga1985 on 2006-12-13
> **kcy29581 said:**
> I haven't tried amaroK, as I was looking for GTK apps (no particular reason though, if amaroK works and it's better, then so be it!)

i wouldn't call it better but it does support other media devices but it will require you to install kde-libs. Just do
```

sudo apt-get install amarok
```
in **gnome-terminal**
Of course, type **y** to install all the dependencies.

---

