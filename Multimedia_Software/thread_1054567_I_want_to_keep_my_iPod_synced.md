---
title: "I want to keep my iPod synced"
date: 2009-01-29
forum: Multimedia Software
---

### Post by fearpi on 2009-01-29
I want to keep my iPod synced with one directory.

That's all.

The directory is /media/green/music, and I want to have a program in which I can set "/media/green/music" as a sync directory, so I can plug in my iPod, open the program, and click Sync.

I have tried gtkpod, and I can't figure out why it's so slow or what the hell it's doing anyway. The documentation is terrible, and its "sync" function seems to be some kind of thing that happens AFTER you manually select what to add to the ipod, and gtkpod (sort of) keeps a list of all the directories that those files happen to be in, and if you "sync" later, it only syncs with directories at the deepest level. Example:

I have /media/green/music/, and its subdirectories are:
AC-DC
Frank Sinatra

So I add /media/green/music to my iPod in gtkpod. But tomorrow I make a new directory, /media/green/music/Pink Floyd. I simply want to sync my ipod to /media/green/music so that it adds Pink Floyd. But as far as I can tell, gtkpod will just sync with:

/media/green/music/AC-DC
/media/green/music/Frank Sinatra

and not with /media/green/music as a whole.

But I can't tell, because the gtkpod options are named so ambiguously and the pre-historic docs are no better.

Banshee is out because it simply ignores a handful of my mp3s when it opens. No idea why.

Quodlibet is out because 1.x simply fails to start due to a HAL error when my iPod is plugged in. And many plugins don't work too well with Quodlibet 2.

---

### Post by fearpi on 2009-02-18
Bump? No good ipod software for linux?

---

### Post by LeakyInkPen on 2009-02-18
I have been toying around with Amarok... Seems to work just fine

---

### Post by Dougie187 on 2009-02-18
There are lots of ipod programs for linux.

Banshee, Amarok, Songbird, Rhythmbox, gtkpod.... All are good for helping sync your iPod, but I don't know if they auto-sync your music.

For future reference, try checking [www.osalt.com](www.osalt.com) if you now a program that does what you want, it will give you alternatives to it, in this case you can look for iTunes.

---

### Post by RaqiGirl on 2009-03-01
> **Dougie187 said:**
> There are lots of ipod programs for linux.

Banshee, Amarok, Songbird, Rhythmbox, gtkpod.... All are good for helping sync your iPod, but I don't know if they auto-sync your music.

For future reference, try checking [www.osalt.com](www.osalt.com) if you now a program that does what you want, it will give you alternatives to it, in this case you can look for iTunes.

The problem, for me, is that none of those support the new Nano 4G.  Apple rewrote the book when they produced the 4G and, so far, there seems to be no way to sync the Nano 4G using Linux.

---

### Post by bapoumba on 2009-03-01
[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)
[http://www.floola.com/modules/wiwimod/index.php?page=WiwiHome](http://www.floola.com/modules/wiwimod/index.php?page=WiwiHome)

---

### Post by linux_lover69 on 2009-03-01
Banshee automatically syncs my ipod nano 4g automatically for me just fine other than it doesn't have album art.

---

### Post by alex6 on 2009-03-04
Hey can someone help me i have an 8gb black ipod nano. I cant seem to put music on my ipod? i drag files into gtkpod and click save then my ipod will say synchronizing the music so i wait for it too stop. I go to listen to music but nothings their? It says in the memory that the music is taking up psace on my ipod but no actual music can be found? whats going on can someone help me please!!

---

### Post by SuperSonic4 on 2009-03-04
> **Dougie187 said:**
> There are lots of ipod programs for linux.

Banshee, Amarok, Songbird, Rhythmbox, gtkpod.... All are good for helping sync your iPod, but I don't know if they auto-sync your music.

For future reference, try checking [www.osalt.com](www.osalt.com) if you now a program that does what you want, it will give you alternatives to it, in this case you can look for iTunes.

Amarok will not automatically sync your iPod but it does sync it manually and I've never had problems with it.

You could try Exaile

---

### Post by ursus262 on 2009-03-08
I find that gtkpod is awkward and unintuitive to use.  In fact I think it's terrible to the extent that I simply can't use it.

I find Amarok is really good, but you need the KDE libraries installed for that to work.  Easy to do though.

For some reason, rythmbox has stopped recognising either of my two music players - one a samsung, the other my ipod.  Strange that!

---

