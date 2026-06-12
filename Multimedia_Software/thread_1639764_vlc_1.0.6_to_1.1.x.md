---
title: "vlc 1.0.6 to 1.1.x"
date: 2010-12-07
forum: Multimedia Software
---

### Post by Tycho59 on 2010-12-07
I am having trouble getting version 1.1.x to install. Doesn't matter if I'm upgrading from 1.0.6 or doing a straight install, I can't get it to install.  Even if i use the terminal or the software center, i can only seem to get version 1.0.6.  What can i do to get around this issue??

---

### Post by TenPlus1 on 2010-12-07
Go into Terminal and type this for 10.04 Lucid:

   sudo add-apt-repository ppa:lucid-bleed/ppa

..or this for 10.10 Maverick:

   sudo add-apt-repository ppa:maverick-bleed/ppa

Then run Synaptic Package Manager and hit the ReLoad button and search for "vlc"

You should find the latest version of VLC available for upgrade :)

---

