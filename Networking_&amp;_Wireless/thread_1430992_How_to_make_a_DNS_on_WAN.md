---
title: "How to make a DNS on WAN"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by C.mind on 2010-03-16
Hi everyone.
My computer is located on WAN and it's considered as a normal user with static IP. I have made a website for my peers in the network and they always connect to it through my Ip address. However, My problem is that I'm not the owner of the WAN server and can't change anything on it . I really want to make it easy for them by memorising word not Ip number.Is there any way that I could make a DNS instead of using the IP. I have tried the command vi /etc/hosts and changed the content to convert my Ip to DNS something like [www.sss.com](www.sss.com) but it only works on my computer not by everyone in the network.I have already installed apache2 on my computer an it runs a server for my website.I don't it to be a global website , I only need it to work the local network.

---

### Post by andrewc6l on 2010-03-16
You'll need to install a DNS server (like bind) and configure it. Here's a (slightly) old doc:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

After that, all the machines on the net will need to set their DNS resolution to your machine's IP address. If they have static IPs that's fairly easy; if they have dynamic IPs they will need to set their machines to use your IP address instead of getting it automatically. Probably it's best to add your DNS as the primary, and the WAN DNS as the secondary so if your machine is down they'll still be able to resolve.

---

