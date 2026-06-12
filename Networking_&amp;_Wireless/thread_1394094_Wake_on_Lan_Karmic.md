---
title: "Wake on Lan Karmic"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by samguili on 2010-01-30
Hello everybody,
I'm a complete newbie on this board, so thanks in advance for the time u may spend to help me deal with my small problems.
So here we are: I m running karmic on a dell optiplex 330, with a broadcom network controller NetLink BCM5787, and wol doesn't want to work since upgrade to karmic.

I have done that : 
```
sudo ethtool -s eth0 wol g
``` and added the line 
```
ethtool -s eth0 wol g
``` to /etc/rc.local file.

This worked just fine on Jaunty. But since the upgrade, it hasn't been working. I tried a fresh install, but it brings the same result.
I somehow think that a driver or something related to the network has changed between jaunty and karmic to explain this problem, but i don't know what i need to do to solve it.

Thank u for your help, it will be greatly appreciated !

---

### Post by samguili on 2010-02-04
hi,
my problem has been solved, thanks to this thread : [http://ubuntuforums.org/showthread.php?t=1380776&highlight=wake+lan](http://ubuntuforums.org/showthread.php?t=1380776&highlight=wake+lan), post n°4 where there's a link talking about dell poweredge. The giving method worked perfectly with my dell optiplex.
here is the link : [http://www.htgi.ca/node/25](http://www.htgi.ca/node/25)
by

---

