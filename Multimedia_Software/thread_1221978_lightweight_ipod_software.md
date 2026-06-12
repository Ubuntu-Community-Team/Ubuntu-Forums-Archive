---
title: "lightweight ipod software"
date: 2009-07-24
forum: Multimedia Software
---

### Post by robfindlay on 2009-07-24
Is there a really lightweight proggy that will let me just manage playlists and moving music onto the ipod w/out needing to a music player?

Like a file manager for the IPOD.

-Rob

---

### Post by Whiffle on 2009-07-24
gtkpod is dedicated to this, although I've found it a little clunky.  Rhythmbox works well though.

---

### Post by robfindlay on 2009-07-24
> **Whiffle said:**
> gtkpod is dedicated to this, although I've found it a little clunky.  Rhythmbox works well though.

all of a sudden Rhythmbox wont let me drag files from a directory into a mounted iPod playlist :-(

---

### Post by Whiffle on 2009-07-24
I think they have to be in Rhythmbox's library first, not just a directory.

---

### Post by philcamlin on 2009-07-24
i use banshee and amarok but amarok is 120 mb banshee is my favorite :popcorn:

songbird works too

---

### Post by robfindlay on 2009-07-24
What I wish someone would write is an inerface that just makes a mounted iPod look to like a drive with folders and files, adn you could just copy them over.  Like most non iPod players.

---

### Post by kpkeerthi on 2009-07-24
gtkpod

---

### Post by philcamlin on 2009-07-24
> **robfindlay said:**
> What I wish someone would write is an inerface that just makes a mounted iPod look to like a drive with folders and files, adn you could just copy them over.  Like most non iPod players.

apple wouldent like that too much

---

### Post by LowSky on 2009-07-24
> **robfindlay said:**
> What I wish someone would write is an inerface that just makes a mounted iPod look to like a drive with folders and files, adn you could just copy them over.  Like most non iPod players.

you can, use rockbox if its a 5th Gen or older ipod and not one of the newer nanos or itouch as they are completely different software
[http://www.rockbox.org/twiki/bin/view/Main/WhyRockbox](http://www.rockbox.org/twiki/bin/view/Main/WhyRockbox)

---

### Post by Grenage on 2009-07-24
Rockbox is great, I used it when I had an ipod.

---

### Post by kpkeerthi on 2009-07-24
When I used rockbox I synced my music library with my iPod using rsync, as simple as

```

rsync -a --modify-window=10 ~/music /media/iPod

```

---

### Post by robfindlay on 2009-07-24
Rockbox wont recognize my ipod...even though teh machine does, and it shows up under media as /media/SLAG'S IPOD

---

### Post by robfindlay on 2009-07-24
> **robfindlay said:**
> Rockbox wont recognize my ipod...even though teh machine does, and it shows up under media as /media/SLAG'S IPOD

helps if you run it as root...silly me.

---

### Post by robfindlay on 2009-07-24
Okay so forgive my ignorance, but what software frontend do i use to build playlists and import new mp3's into say a new playlist?

---

### Post by robfindlay on 2009-07-24
> **kpkeerthi said:**
> When I used rockbox I synced my music library with my iPod using rsync, as simple as

```

rsync -a --modify-window=10 ~/music /media/iPod

```

I tried that command--changed for my setup--and i just get a "failed operation not permitted"

---

### Post by kpkeerthi on 2009-07-25
> **robfindlay said:**
> I tried that command--changed for my setup--and i just get a "failed operation not permitted"

The command does a 'file copy' from a source folder to a target folder. If the files were not copied, it could be a permission issue on the destination folder. 

As I posted earlier that command can be used only if you are using rockbox.

---

### Post by robfindlay on 2009-07-25
> **kpkeerthi said:**
> The command does a 'file copy' from a source folder to a target folder. If the files were not copied, it could be a permission issue on the destination folder. 

As I posted earlier that command can be used only if you are using rockbox.

I have rockbox up and running dandy, my only problem is learning hte new interface, for instance when i load up new mp3's i like to put them into a dedicated playlist, i can sort of do the same thing by putting them into a dedcated folder, but how do you make play specific folder at random OR your entire collection at random?

---

