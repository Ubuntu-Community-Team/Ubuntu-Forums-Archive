---
title: "RhythmBox Remote/Web Interface"
date: 2012-05-29
forum: Multimedia Software
---

### Post by adam.webb on 2012-05-29
Hi All, 

I'm looking for a web interface/way or remotely controlling Rhythmbox which works with the current versions. I used to have this working fine with a server/mediaPC which sits in the corner plugged into my hifi, which I could control either using my smartphone, or via the web browser in my laptop.

This stopped working some time ago, and looking around it looks like the API update which killed the pluggins which were out there. 

Does anyone know of one which works with the current versions of rhythmbox, or alternatively another mediaplayer which I could use similarly? 

I'm running the latest Xubuntu on the mediabox, and gnome3/ubuntu on my laptop, but I dont think that should make much difference.

Cheers

Adam

---

### Post by LewisTM on 2012-05-29
What you want is MPD (Music Player Daemon), which is designed to be remote controlled since it's just a daemon.
Once your have MPD running, you can control it through any number of clients on smartphones (MPod, MPDroid), desktop apps (GMPC, Sonata), Firefox plugin (Minion) or commandline (mpc).
IMO it's the fastest and most powerful way of managing music.
[https://help.ubuntu.com/community/MPD](https://help.ubuntu.com/community/MPD)

Cheers!

---

### Post by adam.webb on 2012-06-16
Thanks very much - exactly what I wanted. Took a bit of fiddling to make it work, but in the end well worth the effort.

Cheers

AW

---

