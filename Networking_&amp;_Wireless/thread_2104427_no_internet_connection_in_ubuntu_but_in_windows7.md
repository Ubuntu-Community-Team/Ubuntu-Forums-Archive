---
title: "no internet connection in ubuntu but in windows7"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by msinfo on 2013-01-13
hi experts,
i have dual boot system with Win7 and Ubuntu 11.04.
before problem internet was working fine on both OS.
two days ago, som cable problem occured, which cable guy troubleshooted by replacing faulty RJ45 connector.
from that point internet is working fine on Win7 but not on Ubuntu.
i have checked IPV4 settings of Ip, DNS, Net mask, they are same on both side.
when i ping default gateway from Win7 it gives response, but from Ubuntu it fails.
 
what i tried : 
disconnected cable for while.
deleted connection and remade connection on ubuntu
 
regards : msinfo

---

### Post by catalin.vasilescu on 2013-01-13
can you try to use 10mb full duplex in ubuntu and see if the prob is same?

---

### Post by msinfo on 2013-01-13
hi, catalin.vasilescu[LIST=1]
[*]thanks, for answer. could you further elaborate that. . .
[*]means how i do that. In win7 i could see this settings in nic configuration pop up box.
[*]how do i change this settings in ubuntu (via commandline, / or gui way)
 
update : i can see pop up notification saying my wired connection connected
but nothing works actually.
i failed pinging my gatway and dns servers, but same works fine in win7
regards : msinfo
[/LIST]

---

### Post by catalin.vasilescu on 2013-01-13
You need ethtool.
In terminal (suppose you use eth0): 

*apt-get install ethtool net-tools*

To see actual configuration of eth0 :
*ethtool eth0*

To change the speed-duplex in 10FD run the command :

*ethtool -s eth0 speed 10 duplex full*

And check again the config of eth0

[I]ethtool eth0


[/I]

---

### Post by msinfo on 2013-01-13
hi,
thanks for necessary info. . .
since my Ubuntu is offline i can't install via online way.
i have downloaded 4 files of version 3.7 from,
[http://www.kernel.org/pub/software/network/ethtool/](http://www.kernel.org/pub/software/network/ethtool/)

how do i install them. . .

regards : msinfo

---

### Post by msinfo on 2013-04-22
Hi,
Thanks to those, who tried answering.
Don't know how, but when today, I boot machine in Ubuntu OS, I could use, my Internet connection perfectly.
This is second time, when a Ubuntu problem, has been solved automatically, without any change in settings, or software.
Note:  I was trying to install ethtool, to diagnose my internet connection  problem, but now, it  has been auto solved. Don't know how?

---

