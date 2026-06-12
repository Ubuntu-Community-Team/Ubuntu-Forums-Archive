---
title: "Network monitoring / bandwidth monitoring tool"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by withjigs on 2011-07-15
Hi all,
We are a small company running half a dozen servers in data center. 
Recently we got charged heavily for over-utilizing the data transfer. So, we are looking for a way to find - uploads and downloads per ip and port basis.
We have mixed environment (Win2008/Ubuntu) so the tool should be able to work for both. 
I am not sure if MRTG provides per port(i.e. application) based analysis.
Any recommendations would be appreciated!
thanks,
Jigar

---

### Post by jmoorse on 2011-07-16
Have you checked out cacti?  [http://www.cacti.net/](http://www.cacti.net/)

---

### Post by withjigs on 2011-07-17
Hi jmoorse,
Thank you for you reply.
I have tried Cacti. But couldn't figure out how to graph the per protocol/port analysis.
If someone can just hint me in that direction, that would be great.
Thanks,
Jigar

---

### Post by jmoorse on 2011-07-17
You should take a look at this:

[http://docs.cacti.net/plugin:flowview](http://docs.cacti.net/plugin:flowview)

It likely has more than a few dependencies (netflow on switch/router, etc) so I would encourage you to pursue this with Cacti.

Going another direction, you may want to take a look at [http://www.ntop.org/overview.html](http://www.ntop.org/overview.html) too.

---

### Post by withjigs on 2011-07-19
Thanks a lot jmoorse. Ill try the Cacti plugin. looks like we have a winner!

---

