---
title: "Ubuntu Windows Networking FAIL"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by Combat on 2010-02-01
Hi, I'm running Ubuntu 9.10. I am hooked into my home network with several windows machines attached. On a daily basis i browse the network and use network shares. Today, I can't. Today i can't see any other machines from ubuntu. I haven't changed any settings in Ubuntu, and nothing has been changed on the network, but yesterday it worked fine and today it doesn't. Anyone got any idea what the problem could be?

---

### Post by johnson.d on 2010-02-08
While accessing through places -> Network in Ubuntu the view of computer changes as per the connections made to the servers present in the network. However if you are able to view the icon named Windows network you can browse through it and access the share. And also you can perform these checks

1) Try connecting the server through Places-> connect to server by entering the ip-address of the system and entering the login credentials.

2) You can use the command to find the shares that are connected to your system
$ smbclient -L localhost

---

### Post by Combat on 2010-02-08
It actually fixed itself. After about 3 or 4 days it just randomly started working again.

However, while it wasn't working, i tried all that to no avail.

---

