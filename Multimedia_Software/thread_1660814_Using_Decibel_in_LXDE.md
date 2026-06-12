---
title: "Using Decibel in LXDE?"
date: 2011-01-05
forum: Multimedia Software
---

### Post by ~Maxx on 2011-01-05
Hello all.  I'm pretty new with Ubuntu in general, and hoped someone could help me out...

Lubuntu comes default with Aqualung - which I'm certainly happy with.  Unfortunately it doesn't yet support Last.fm, so I'm auditioning new players.  The first (and only - so far) that I've installed is Decibel.  I quite like the look of it so far.  It has the features I need without the bloat.  Unfortunately I can't get it to work.  When I select a track or tracks from the CD drive (yes - I still listen to CD's :p) the track shows up in the playlist and the disc spins in the drive for a second or two, but I get nothing.  Just a red X next to the track in the playlist.  And tracks on my hard drive don't even show up in the explorer module.  And no info is retrieved from cddb (I do have that option selected).

From what I've read Decibel is geared toward GNOME users, and based on Python.  Python appears to be installed by default in Lubuntu, so I'm going to assume that Lubuntu lacks something else that GNOME has which will allow this thing to operate.  But I have no idea what that might be.

Has anyone managed to use Decibel on LXDE?  Thanks in advance for any advice...

---

### Post by BicyclerBoy on 2011-01-06
And you can play CDs with some another app?

cdplay play 1

If not then check you are a member of the cdrom group

What format are the tracks on the HDD ?

I use "abcde" to rip CDs to ogg or flac.
But the std rhythmbox player can rip to HDD.

---

### Post by ~Maxx on 2011-01-06
Ahh yes...  Sorry I left that bit of info out.  Aqualung seems to be working fine.  It plays CD's and WAV files anyway, and I've used it to rip a disc (to WAV).  Haven't tried any other file formats yet.

Just got home from work, so I'm going to give a couple of other players a try and see what happens.  Thanks BicyclerBoy.  

And by the way...  If anyone has any suggestions for LXDE music players I'd sure appreciate them.  I've read about most of them, but documentation for use with LXDE and Lubuntu is scarce at best.  I just need a light, simple player that supports a few typical formats (wav, mp3, flac, & ogg are about all I use),  has an eq, and Last.fm support.  Album art would be nice too, but not really necessary.  

Thanks again!

---

### Post by cavalier911 on 2011-01-06
**_DeaDBeef_**
```
sudo add-apt-repository ppa:alexey-smirnov/deadbeef
```
```
sudo apt-get update
```
```
sudo apt-get install deadbeef
```

Help/Help
Edit/Preferences/Plugins/highlight Plugin/Configure

---

### Post by ~Maxx on 2011-01-06
DeaDBeef was next on the list Cavalier911.  I should have started with this one!  More than happy with it!  Thanks!

---

