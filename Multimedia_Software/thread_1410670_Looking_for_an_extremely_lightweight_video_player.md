---
title: "Looking for an extremely lightweight video player"
date: 2010-02-19
forum: Multimedia Software
---

### Post by dsavi on 2010-02-19
I have this 12 year old laptop that has a considerable battery life (On the better side of two hours) for its age, and I'd like to play AVIs on it. Totem works fine, but every 45 minutes or so the framerate drops to about half of what it should be. Is there any video player that could give me better performance? (I already use totem in Xterm instead of GNOME to save resources)
The laptop has a 366mHz processor and 256mb of RAM.

---

### Post by rahul23 on 2010-02-19
use 
[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)
(pick up a older version)

this player can play anything and extreamly light , i used it on my windows when i had a pc with 128 mb ram

---

### Post by dsavi on 2010-02-19
Thanks, I'll give that a try. Does anyone have any other tips on reducing resource usage by other applications more than logging into safe xterm?

---

### Post by VertexPusher on 2010-02-19
> **rahul23 said:**
> (pick up a older version)
No, pick up the latest version.

MPlayer isn't one of those freeware/shareware apps for Windows which get slow and bloated over time. Its performance has improved, not degraded. If there are features in MPlayer that you think you don't need, you can disable them at compile time to reduce the size of the executable. This is the proper way to go, not picking up older bug-ridden versions.

---

### Post by Jose Catre-Vandis on 2010-02-19
You need to visit KMandla's blog on running low spec laptops and using the CLI as your main interface:

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)
[http://kmandla.wordpress.com/software/](http://kmandla.wordpress.com/software/)

---

### Post by dsavi on 2010-02-19
^ I had been there before but lost the name of the site and didn't have time to do his screen-vs patch, thanks.

With which options should I configure mplayer in order to get just what I need?

---

### Post by andrew.46 on 2010-02-19
Hi dsavi,

> **dsavi said:**
> With which options should I configure mplayer in order to get just what I need?

This guide may give you a few ideas:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

All the best,

Andrew

---

### Post by dsavi on 2010-02-19
Now it's just to disable X11, a bit off topic but I don't want to create another topic. I can't find how, all the methods documented elsewhere are outdated (My guess is that it's due to upstart's new system of doing things).

I tried using sysv-rc-conf to disable gdm, but gdm is already disabled. If I disable x11-common, would that work?

---

