---
title: "How to use Iptables to block Limewire? (and P2P generally)"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by qprfact on 2009-12-27
Is there a particular port I can block to do this? I want to lock down access on my home network, but still allow http

Thanks

---

### Post by clam2000 on 2009-12-28
for peer to peer generally there isn't any set of ports you can block, and you'll need to actually look at the contents of the packets to determine if they should be blocked.

Limewire defaults to using port 6346, but it will also dynamically select other ports if that is blocked, so it is unlikely to do much good.

You might consider looking into OpenDPI ([http://code.google.com/p/opendpi/](http://code.google.com/p/opendpi/))
It claims to do what you want, but I haven't had experience setting it up or getting it to work with IPTables.

---

### Post by byStanderone on 2009-12-28
...have you tried ufw to deny that particular ip?

---

### Post by anonSam on 2009-12-28
clam2000 is right. You would need something that could recognize the specific packet protocol for each type of p2p network. The p2p community in general has learned to change the default ports in their clients just to avoid this sort of thing. Wish I could be more helpful but I can tell you that blocking a set of ports will most likely not stop any p2p activity. Also lets say you blocked every port except http, someone could still configure their client to use port 80.

---

### Post by qprfact on 2009-12-29
I have gone for a highly low tech solution for the time being - a cron job that runs every hour replacing the Limewire startup script with a blank file of the same name!

---

