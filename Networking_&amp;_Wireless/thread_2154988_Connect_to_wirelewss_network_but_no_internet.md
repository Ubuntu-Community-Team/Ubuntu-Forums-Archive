---
title: "Connect to wirelewss network but no internet"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by Subcomfreak on 2013-06-16
Hi all, I'm running Xubuntu 12.04 with a windows 7 duel boot on an ASUS U47VC . Recently I had a crash on the windows side of my system so I was forced to restore part of it by bringing coping over some cloned windows partitions from an external hard drive. For some odd reason I was unable to boot to Linux after I copped the partitions over so I ran boot repair and now I'm able to boot okay... booting isn't my problem. 

Before the crash everything worked fine but now I can connect to the wifi network, but I do not have internet access. When I try to update my machine it simply says it cannot retrieve the data. When I try to open up firefox it does not load the web page. I have tried to delete the connection and start with a fresh connection with no luck. I can connect fine, but I don't have any access to the internet.


Is there any generic solution to this problem? DO you need specific log files or terminal outputs? I can provide any information you need....

---

### Post by Subcomfreak on 2013-06-16
I was able to solve this by changing the DNS server to google's (sudo gedit etc/resolv.conf and replacing the entry with 8.8.8.8).

---

