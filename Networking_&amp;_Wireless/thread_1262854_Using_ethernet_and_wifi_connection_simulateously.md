---
title: "Using ethernet and wifi connection simulateously"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by maciejk on 2009-09-10
Hi, 
        I have the possiblity to connect to two independent sources of internet, one is ethernet cable, the other is wifi. Is there a possibility two use them at once. I mean, For example I would like to run wget using one connection, and second wget download with the other?

---

### Post by jward3010 on 2009-09-10
Someone correct me if I'm wrong but I'm pretty sure Ubuntu can't handle simultaneous connections (through Network Manager anyway). It will just pick one or the other (not sure how it prioritises).

To be honest theres no real advantage to doing such a thing especially if the files you're downloading are out on the internet, your broadband connection speed will limit you regardless and you wont use up extra resources in creating and maintaining a connection.

---

### Post by maciejk on 2009-09-10
I think there should be gain in speed, the two source are completely independent, from different internet suppliers.

---

### Post by stone[no] on 2009-09-10
[http://www.gentoo-wiki.info/Dual_internet_connections](http://www.gentoo-wiki.info/Dual_internet_connections)

This might help...

---

### Post by Iowan on 2009-09-10
There is at least one other thread around here about using two interfaces simultaneously. I'll see if I can find a link... but yes, Network Manager will only manage one interface at a time, so the other one would need to be set up in */etc/network/interfaces*, then some massaging of the routing table.

[Here]("http://ubuntuforums.org/showthread.php?t=1210177") is one.
[This]("http://ubuntuforums.org/showthread.php?t=1108658") one didn't really get solved.

---

