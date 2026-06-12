---
title: "SSH Cannot bind to port"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Hellmark on 2009-11-20
Ok, I use SSH tunnels, and for a long time I've used GSTM to easily manage these tunnels. However, recently, I've been having problems where it connects, but the tunnel isn't created because it cannot bind to a port. If you run things from the commandline you get back 

> bind: Cannot assign requested address


Now, I've seen previous posts on the matter, and one said that /etc/networking/interfaces may have "iface lo inet loopback" commented out, or something along those lines. auto lo and the iface line are there. If I use ifconfig to put down lo, then bring it back up, I can then create the tunnel.

What can I do to fix this, short of a kludge boot script that cycles lo?

Running KDE4, with Kubuntu 9.10.

---

