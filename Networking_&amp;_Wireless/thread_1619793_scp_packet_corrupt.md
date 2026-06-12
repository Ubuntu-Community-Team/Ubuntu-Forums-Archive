---
title: "scp: packet corrupt"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by hoover67 on 2010-11-12
Hi folks,

sometimes when transferring large files using scp between my desktop running maverick and other servers running Ubuntu, Debian or CentOS, I get the following error message: 


[FONT="Courier New"]77%  258MB  11.3MB/s   00:06 ETAReceived disconnect from xxx.xxx.xxx.xxx: 2: Packet corrupt[/FONT]

I've found a seemingly related bug report on launchpad here: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/60764](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/60764)

but the provided "ethtool" fix did not help. I'd be most grateful for any ideas on how to solve this issue. Some more info: 

[FONT="Courier New"]Linux lotus 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux
lspci | grep eth -i
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)[/FONT]

TIA, Uwe

---

### Post by Eric Buist on 2011-01-22
I am experiencing similar problems, over wi-fi connection. I thought this was my wi-fi setup, which is very unstable. I tried many different alternatives without too much success. But this post makes me believe there is yet another bug in Ubuntu that will need a version upgrade to get a fix for. I am very surprised no one can provide any hint about how to work around this. I am facing the same trend, whatever problems I am faced with.

---

