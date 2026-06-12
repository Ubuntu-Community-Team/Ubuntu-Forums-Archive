---
title: "System halts if network mount is missing"
date: 2008-05-29
forum: Mythbuntu
---

### Post by uMuppet on 2008-05-29
I am mounting my music, photos, and _some_ videos from a network location on boot using the following lines in /etc/fstab

```
//192.168.1.10/Photos /var/lib/mythtv/pictures cifs defaults 0 0
//192.168.1.10/Music /var/lib/mythtv/music cifs defaults 0 0
//192.168.1.10/Movies /var/lib/mythtv/videos/Network cifs defaults 0 0

```

This works great, unless the network PC is not powered up or connected.  When I enter Mythvideo it locks up waiting for that drive to be ready.

Is there a way that I can ping the network place before opening mythvideo and then either connect or disconnect the network mount?

---

