---
title: "Networking local host for supercomputer"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by Yu Jin X5 on 2013-03-12
I am looking to set up a local network so that I can run a Linux supercomputer. But, I am having trouble what program should I use or is there any good websites I have looked it up but am still having trouble. I will consist of 3 computers with different motherboards so that can be troubling it will 9.6 gigaflop of cpu power 6 gb of ram 2 per unit and will be held together with gigabit speed Ethernet local connection and gigabit speed internet.

---

### Post by RoosterHam on 2013-03-13
Are you looking for a program to set up the HPC network? or looking for the software to direct and distribute processing?

configuring the network doesn't require extra software, base installation of most distributions will provide all networking tools you could ever need. 

One style of HPC linux cluster is a Beowulf cluster. See following links just as a starting point.
[http://en.wikipedia.org/wiki/Beowulf_cluster](http://en.wikipedia.org/wiki/Beowulf_cluster)
[http://linuxadvanced.blogspot.com.au/2012/04/building-beowulf-cluster-with-ubuntu.html](http://linuxadvanced.blogspot.com.au/2012/04/building-beowulf-cluster-with-ubuntu.html)
[http://byobu.info/wiki/Building_a_simple_Beowulf_Like_Cluster_with_Ubuntu](http://byobu.info/wiki/Building_a_simple_Beowulf_Like_Cluster_with_Ubuntu)
[http://www.linuxquestions.org/questions/linux-newbie-8/beowulf-cluster-on-ubuntu-10-04-a-818999/](http://www.linuxquestions.org/questions/linux-newbie-8/beowulf-cluster-on-ubuntu-10-04-a-818999/)

other
[http://www.admin-magazine.com/HPC/Articles/Warewulf-Cluster-Manager-Master-and-Compute-Nodes](http://www.admin-magazine.com/HPC/Articles/Warewulf-Cluster-Manager-Master-and-Compute-Nodes)
[http://wiki.debian.org/HighPerformanceComputing](http://wiki.debian.org/HighPerformanceComputing)

---

