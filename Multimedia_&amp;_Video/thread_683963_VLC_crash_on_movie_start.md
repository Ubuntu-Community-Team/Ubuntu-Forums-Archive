---
title: "VLC crash on movie start"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by openjoel on 2008-01-31
Hi, I just got my new computer ( an acer travelmate 6292 laptop ).
And I just wanted to watch a movie.

First I tried MPlayer, then Totem but both of them just crash when I try and start the movie.. witch is in .avi format.
So I thought vlc has never failed me before, lets try vlc.
Same thing there it just ajust itself for the movies resolution then just crash.

Running it in the terminal with "vlc /path/to/avi.avi" gives me:

VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

 :confused:

Any one have any clue?
This is a fresh install of Ubuntu 7.10.
Read around on the internet and maby you guys wanna know what video-card I use so: Intel (santa rosa) GMA 3100 (I think it's called that any way.)

---

### Post by ubuntu-freak on 2008-01-31
> **openjoel said:**
> Hi, I just got my new computer ( an acer travelmate 6292 laptop ).
And I just wanted to watch a movie.

First I tried MPlayer, then Totem but both of them just crash when I try and start the movie.. witch is in .avi format.
So I thought vlc has never failed me before, lets try vlc.
Same thing there it just ajust itself for the movies resolution then just crash.

Running it in the terminal with "vlc /path/to/avi.avi" gives me:

VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

 :confused:

Any one have any clue?
This is a fresh install of Ubuntu 7.10.
Read around on the internet and maby you guys wanna know what video-card I use so: Intel (santa rosa) GMA 3100 (I think it's called that any way.)

 
Sure you're not missing a package or few? Install the essential packages in part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) just incase. 
 
Nathan

---

### Post by jjgomera on 2008-02-01
maybe the problem is only with this avi, do you have same problems with others avi files?

---

### Post by Migoo on 2008-03-20
My guess is that you have problems with your drivers. I have a Dell D830 with integrated Intel 965GM graphics card. I run Compiz Fusion but I have to use Xgl instead of the intel-driver to be able to look at films.
But I have managed to make mplayer run. Just add the following line to the file &#711;/.mplayer/config

vo=x11

And then start mplayer from the console and see if it works. I have not found any solution for vlc, wich is my favorite, yet but I'll keep up the search :)

//Kamijo

---

