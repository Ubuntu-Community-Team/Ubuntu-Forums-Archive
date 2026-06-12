---
title: "how to connect ubuntu11.04 with windows 7 through  crossing cable"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by spkanu on 2011-11-16
how to connect ubuntu 11.04 with windows 7 for file sharing through crossing cable.

i have checked in the forum but i can't find any solution regarding these.

---

### Post by surfer on 2011-11-16
you need to configure your 2 computers to have an ip address in the same subnet. e.g.:

win7: 192.168.0.10
ubuntu: 192.168.0.11

this way you have an ip connection between the computers (if your network interfaces are sufficiently new, you don't even need to have a crossed cable; the interface will figure out how to connect).

in order to exchange files you need to have a server on one of the machines. the simplest would be to install ssh on the linux machine, connect from the windows machine and exchange files ([winscp]("http://winscp.net/") may be an option).

of course you could also use samba, ftp or any protocol of your choice.

---

