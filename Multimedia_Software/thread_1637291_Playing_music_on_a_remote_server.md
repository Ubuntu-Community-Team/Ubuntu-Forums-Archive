---
title: "Playing music on a remote server"
date: 2010-12-04
forum: Multimedia Software
---

### Post by honeysett on 2010-12-04
I have an Ubuntu 10.04 desktop PC (desktop) that I access remotely, i.e. with no monitor and keyboard attached. I do this by making an ssh connection to "desktop" from my laptop (also running Ubuntu 10.04).

I have all my music stored on "desktop" and I want to play this remotely through the soundcard on "desktop" which is attached to a hi-fi amplifier, from my laptop.

How can I do this?

I tried running, say, rhythmbox, on "desktop" through ssh X11 forwarding to my laptop but cannot play music - it says that the right codes are not installed although they are because I can use rhythmbox on "desktop" directly (attaching a monitor and keyboard to it).

---

### Post by MetalMusicAddict on 2010-12-04
You absolutely want to use [MPD]("http://mpd.wikia.com").

You can set it up on your Ubuntu box and output it through the local soundcard. Then, use a "client" on any OS to control what music plays.

Dig into MPD. Lots of info out there. I'm sure you'll love it.

---

### Post by as2003 on 2011-05-27
I have a similar problem.

If I play music on the local machine, using cli mplayer, I hear the music.

But if I SSH into that box and issue the same command, I hear nothing. Is there a simple way to fix this?

I don't want to have to install extra software...

Thanks for any advice.

---

### Post by chris1497 on 2011-07-07
I'm also interested in MPD.  Can anyone point me towards a recent tutorial.  I've been looking around quite a bit and all I can seem to find is old stuff for ubuntu 6.xx and stuff from 2005 2006.  I've tried following them but haven't been able to get it to work

---

### Post by chris1497 on 2011-07-07
this did the trick on 11.04

[http://gmpc.wikia.com/wiki/MPD_INSTALL_USER_SERVICE_UBUNTU](http://gmpc.wikia.com/wiki/MPD_INSTALL_USER_SERVICE_UBUNTU)

now to setup icecast...

---

### Post by dankdave on 2011-09-25
I'm in an identical scenario.  I have a standalone box that I would like to use for playing music either at home or remotely.

Any suggested reading above and beyond mpd for setting up a music server?

---

