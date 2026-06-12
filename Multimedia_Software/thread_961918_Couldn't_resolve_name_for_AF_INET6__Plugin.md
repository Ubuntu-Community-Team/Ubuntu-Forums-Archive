---
title: "Couldn't resolve name for AF_INET6 / Plugin"
date: 2008-10-28
forum: Multimedia Software
---

### Post by Aen107 on 2008-10-28
Hello community,

Even though I have installed every codec suggested in the sticky I am not able to play the videos from this site.
[www.bloomberg.com](www.bloomberg.com)

Interestingly the live stream works, but the Editors' Video Picks do not!

I have ubuntu 8.04 on a T400 with radeon graphics.

I use media-player connectivity:

With gmplayer i get: Couldn't resolve name for AF_INET6: [www.bloomberg.com](www.bloomberg.com)
with totem-xine i get something like: necessary plugin not available. (translated from German)

Every other video on the inet works perfectly; Except this one, which I am the most interested in (:

Any suggestions?

thanks

Aen

---

### Post by attilahooper on 2008-11-11
I have the same problem. When totem/codecs and plugins are installed I get no sound. When i put the URL into Mplayer I get AF_inet6 error.

---

### Post by WhErEeVeR on 2009-01-04
If you enter the below line in your ~/.mplayer/config file it won't give you this error any longer.

prefer-ipv4 = yes

---

