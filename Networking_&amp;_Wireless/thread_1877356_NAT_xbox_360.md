---
title: "NAT xbox 360"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by Cordeth on 2011-11-08
So i am runnin ubuntu 10.10 on a laptop and have it connected to my xbox. My internet is being provide by a verizon 3g mifi through usb. I got my xbox working with live but my NAT is moderate. My question what is the easiest way to set my NAT to open for my xbox? I have searched and searched but have yet to find an anwsert that works and is also easy. Thnx

---

### Post by Cordeth on 2011-11-10
No one can help? This sucks.

---

### Post by jonobr on 2011-11-10
Hey there,


I , the great Carnac, hear your problems,
I used the dark arts, combined with powerful voodoo rituals,
I drew a pentangle on the floor, sat in the middle and began ancient incantations,


In the end, I went to google and typed "ubuntu xbox open nat"
[Links like this were returned]("http://ubuntuforums.org/archive/index.php/t-538796.html")

There is a lot of comments on whether it works or it didnt, but they all seem to agree that 
The full set of ports that need to be opened for Xbox live to work are:

TCP 80
UDP 88
UDP 3074
TCP 3074
UDP 53
TCP 53

The user pmcchapman in the thread above, gives your exact config and the same steps he took and goes on to answer other users issues.

See ? Who needs voodoo when you got googoo (le)

---

