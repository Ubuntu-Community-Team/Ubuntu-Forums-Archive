---
title: "media center - low hardware requirements"
date: 2011-12-10
forum: Multimedia Software
---

### Post by robfromdublin on 2011-12-10
I would like to convert my girlfriends old laptop to a media center but it is not powerful enough to run xbmc.

I've installed enna & canola to have a play around with them but neither appear to be under development anymore.  Are there any other light media center apps that I could try?

Not sure what the graphics card is but xbmc just gave me a blank screen when I opened it so I'm guessing it can't handle 3D rendering.  CPU is 1.6GHz Intel T1300, RAM is 512MB, running 10.04 LTS.

---

### Post by WasMeHere on 2011-12-10
Hi robfromdublin

Well, that is a tough task. I think you must select a very light desktop environment. Lubuntu is the lightest one in the Ubuntu family with LXDE. This will give you more power for the multimedia software. I guess VLC or mplayer can do a good job with a small CPU. I think you have no chance to view full HD (1080/50p) not even with a new graphics card and hardware acceleration, and maybe you have to decrease the resolution to 720/30p or lower.

Another possibility is to download GeeXbox and run it as a live session (it has its own embedded linux system) from a CD or USB drive. It costs very little to try :-)

My recommendation would be to use a better computer for media center and use the old one for the internet, editing texts etc. That should work very well with Lubuntu.

Have fun finding out what you can do with [KLX]ubuntu :-)
Olle

---

### Post by robfromdublin on 2011-12-11
Cheers for the reply Olle.

Geexbox uses hbmc unfortunately so I think that's not a go-er.  I'll give it a shot though, can't hurt. 

Yeah I think it might be optimistic running a media center with this.  It's not really for HD movies or anything so not too fussed about that, just for music & photos.  Maybe the odd sports stream. 

I'll keep having a play anyway.

---

### Post by WasMeHere on 2011-12-11
In order to get a good multimedia experience in Ubuntu, do the lesson on the following thread:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=766683_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

After your reply I suggest ***VLC*** and ***mplayer*** again. You can run mplayer from the command line, and there are many options to make a video run better
```
alias mplayerlavd='mplayer -lavdopts fast:skiploopfilter=nonref -fs'
```
You find more help via
```
man mplayer
vlc -h, --help
vlc -H, --full-help
```
For example run ```
man mplayer
``` and look for VIDEO OUTPUT DRIVERS.

---

### Post by WasMeHere on 2011-12-11
... and for
- photo management I suggest ***digikam***
- photo editing I suggest ***gimp***

If you increase the RAM to 1,5 GB or 2 GB, the computer will be much better both for video and photos. Then it might run well enough will Ubuntu 10.04 LTS, so no need to learn Lubuntu.

But I certainly recommend that you try Lubuntu anyway. It is fast and has new drivers and libraries, so that you get new versions of software (in priciple 18 months newer than those of 10.04).

---

### Post by BarryDocks on 2011-12-11
I have xbmc running on a slower machine than that, it did take a while to sort out the graphics issues but it is possible - the solution will depend on the graphic hardware you have, ie intel, ati or nvidia.  You will need to customise the xorg(?) files.  It won't stream video, I use it in the kitchen for photos and music.

You could also try [openelec]("http://www.openelec.tv/") which is a custom lightweight linux distro designed for xbmc and can be run on slow hardware

---

