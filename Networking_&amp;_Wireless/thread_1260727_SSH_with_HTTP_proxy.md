---
title: "SSH with HTTP proxy"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by marshmallow1304 on 2009-09-07
I'm trying to use KTorrent with both HTTP and SOCKS proxies via SSH.  I know how to use SOCKS with dynamic forwarding, but how do I set up the SSH connection so it works as an HTTP proxy?



[size=4]Edit: I ended up installing squid on my server, which made it a lot easier.[/size]

---

### Post by kevdog on 2009-09-08
Take a look at this:
[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

### Post by marshmallow1304 on 2009-09-08
Maybe I'll try tsocks or proxychains.  Is one intrinsically better than the other?

---

### Post by marshmallow1304 on 2009-09-08
KTorrent was freezing up on me, so now I'm trying Deluge with tsocks.  I can connect to trackers and get seeder/peer counts, but Deluge never connects to any seeders/peers.

---

