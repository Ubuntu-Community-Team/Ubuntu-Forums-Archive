---
title: "Ubuntu 10.04 LTS wired internet issues"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by TuxWithoutPants on 2010-06-02
I'm running Ubuntu 10.04 on wubi, having problems with my internet connection. When I cold boot into ubuntu, I have no internet on my wired connection. However, if I boot into windows first, then restart as ubuntu, the connection is fine.

Any suggestions? Good advice will be much appreciated.

---

### Post by Iowan on 2010-06-02
If you boot directly into Ubuntu, what are results of **ifconfig -a**?

---

### Post by Mad-One on 2010-06-02
What's in your /etc/network/interfaces file? It sounds as though your NIC isn't being initialised at boot.

---

### Post by sengiv on 2010-09-28
Hey guys!

I experienced the same problem, when i installed ubuntu 10.04 live installation. also, downloading the ISO
The network manager not functions properly that comes with online
like from ubuntu.com.


After that i installed ubuntu from CD, which i got from some distributor & now its everything fine in connecting network.

you can see the connection status from the network manager icon presents in top-right hand side of panel.

Hope this might resolve your problem :)

---

