---
title: "[SOLVED] Banshee and music player applet won't play nice"
date: 2008-12-18
forum: Multimedia Software
---

### Post by GeorgeMurango on 2008-12-18
I'm running Ibex, and for some reason my music player applet won't work with banshee. I use the applet a lot, and I've been switching over to rhythmbox, but recently I've been using banshee again, and the player applet just won't recognize it. I don't know if I need a custom command for the plugin, I've only tried dbus activation. Also, if there;s a visualizer for banshee, let me know.

---

### Post by GeorgeMurango on 2008-12-24
I apologise for bumping my own thread in advance, but I would really like to be able to do this.

---

### Post by lassegs on 2008-12-27
Hi,
I like your taste in music players. I had this problem and found an easy solution.

_The problem:_ music-applet in intrepid repositories is version 2.3.x something, and supports only the legacy (before v 1.0) banshee player. Support for banshee v 1.0 and up was added in music-applet 2.4.0

_The solution:_ Install the newest version of music-applet, 2.4.2

_How to install_
I tried compiling from source, but it had some dependencies I didnt have the time to resolve, so i found the quick (and maybe dirty?) solution:
Download the .deb packaged for next version of Ubuntu, Jaunty
[http://launchpadlibrarian.net/19435921/music-applet_2.4.2-1_i386.deb]("http://launchpadlibrarian.net/19435921/music-applet_2.4.2-1_i386.deb")
Double click, install.

This should solve your problem. Have a rocking new year with banshee :)

---

### Post by GeorgeMurango on 2008-12-28
Thanks. That solved it.

---

