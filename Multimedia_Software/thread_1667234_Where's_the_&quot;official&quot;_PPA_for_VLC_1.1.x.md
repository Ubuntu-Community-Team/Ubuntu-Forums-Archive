---
title: "Where's the &quot;official&quot; PPA for VLC 1.1.x?"
date: 2011-01-14
forum: Multimedia Software
---

### Post by emarkay on 2011-01-14
I see this:[http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html](http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html), and I gut busted with the  [n-muench/vlc PPA]("https://launchpad.net/%7En-muench/+archive/vlc/+packages") issue - (aargh!)

---

### Post by mc4man on 2011-01-14
There is this new deal about ppa's for lucid backporting maverick libraires for their vlc builds.
It's a bit unfortunate because they could certainly do a good 1.1.X build using the 0.5.X ffmpeg libs.

If you are using one of these ppa's on lucid then adding this ppa will fix any gstreamer issues (and is a good thing to do on lucid anyway
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

This ppa will fix mplayer and give you a current mplayer build
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

I would term the above ppa's as highly trusted

Otherwise building your own is the best way.

For maverick and natty there is this 'semi official' ppa for the current 1.2+ vlc
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

---

