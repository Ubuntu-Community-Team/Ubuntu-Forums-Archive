---
title: "make wicd autoconnect without logging into pc???"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by wynneth on 2009-07-04
I recently put my old desktop box <fileserver lol> on Ubuntu 9.04, and installed wicd (because I hate nmapplet). I use this box for various things, so I like being able to ssh into it. I would like to be able to do this even if the machine reboots (power failure), but it seems thus far that it will not connect before a local login. Apparently I can specify the connection in /etc/network/interfaces but that's not really the proper way and if I do that then it comes online just until I get to a login screen and then it goes offline...

Anyway I'm willing to go another way if anyone has pointers, the point is I want to be able to access the machine via ssh, network filesharing, and if I could without the login - even remote desktop/vnc -  WITHOUT LOGGING IN LOCALLY. Note, autologin does not accomplish what I want as the pc needs to remain locked at all times.

---

