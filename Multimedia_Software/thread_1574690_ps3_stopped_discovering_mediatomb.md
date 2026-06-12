---
title: "ps3 stopped discovering mediatomb"
date: 2010-09-14
forum: Multimedia Software
---

### Post by lawfultoad on 2010-09-14
i've had my ubuntu server 10.04/mediatomb/ps3 setup for a long time and suddenly today, it stopped working.

no changes have been made, the ps3 simply does not discover mediatomb.  the ps3 does discover windows media servers that are also on the network.

ps3 has wired ip address and active connection
ubuntu has wired ip address and active connection
mediatomb ui is accessible
sudo /etc/init.d/mediatomb restart
sudo shutdown -r now
kill -9 mediatombpid
sudo /etc/init.d/mediatomb start
verified no changes were made to /etc/mediatomb/config.xml
searched for media servers on ps3 x 100 in between, no luck

any ideas?

thanks!

---

### Post by lawfultoad on 2010-09-15
So many views, no responses. :(

---

### Post by lawfultoad on 2010-09-18
I resolved it.  Mediatomb randomly bound to a virtual interface instead of eth0.  Adding <interface>eth0</interface> to the config file fixed it.

---

