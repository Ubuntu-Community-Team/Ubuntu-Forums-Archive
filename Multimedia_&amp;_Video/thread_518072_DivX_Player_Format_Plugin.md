---
title: "DivX Player Format Plugin"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by Ingla on 2007-08-05
Hello.

I'm running a new Feisty installation and most streams seem to work fine (I've installed all the codecs, etc. from Automatix or Synaptic that I could find.

However, there's a site ([www.myseries.nl](www.myseries.nl)) designed for DivX Player which says a plugin is missing. Of course the install can't find it and the manual install takes you to the player's site. But no plugins are available for Linux.

On their test page it says "For Linux support try Mplayer. I have Mplayer and the Firefox plugin picks up most normal stuff, but it doesn't kick in for this. 

Anyone know how to get this working (if it's possible)?

Thanks.

---

### Post by Gremlinzzz on 2007-08-05
Use mplayer plugin and put these commands in terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
:guitar:

---

### Post by Ingla on 2007-08-05
Never mind. I found the answer here:

[https://bugs.launchpad.net/ubuntu/+s...in/+bug/112055](https://bugs.launchpad.net/ubuntu/+s...in/+bug/112055)

Hope this helps if anyone has the same problem.

---

