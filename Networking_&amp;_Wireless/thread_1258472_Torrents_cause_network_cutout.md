---
title: "Torrents cause network cutout"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by deadstop on 2009-09-05
Hi,

I'm running Jaunty with an intel 2200 wireless card.

Everytime I open up my torrent program (I've so far used vuze, transmission and Ktorrent. With the same results each time, so the problem isnt the program. I dont think) my network speed drops dramatically after a few seconds. Although the only indication I get of this is that the torrent download drops to 0kb/s and internet browsing doesn't work. This happens with both wireless and wired networks. 
So far I've installed WICD, forwarded a whole bunch of ports, installed the backports. All to no avail. At first I assumed it had something to do with the amount of traffic on my network causing it to somehow fail, but I can download some stuff at +600kb/s no problems, just not torrents. 

Thanks :)

---

### Post by drazelian on 2011-06-06
I am having the exact same problem on 11.04.
help would be appreciated

---

### Post by nbound on 2011-06-06
Similar problem here, could be related?

[http://ubuntuforums.org/showthread.php?t=1775726](http://ubuntuforums.org/showthread.php?t=1775726)

---

### Post by SeijiSensei on 2011-06-06
Often it's a router problem.  Try limiting the number of *simultaneous connections* (not up/down speeds) to 50 or so.  If you find that pulling the power cord from the router and restarting it fixes the problem, this is the likely cause.

---

### Post by nbound on 2011-06-06
> **SeijiSensei said:**
> Often it's a router problem.  Try limiting the number of *simultaneous connections* (not up/down speeds) to 50 or so.  If you find that pulling the power cord from the router and restarting it fixes the problem, this is the likely cause.

In my case this is not the reason, it will do it on torrents where im downloading from only 5, 10, etc peers, and there isnt even 50 peers/seeders total. Previously my limit was 250/torrent and like 1000 max, never had any problems then

---

