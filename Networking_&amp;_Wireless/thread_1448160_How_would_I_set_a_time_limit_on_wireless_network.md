---
title: "How would I set a time limit on wireless network?"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by toucher5 on 2010-04-06
I am currently sitting at wifi hotspot and was promted by a cgi file that I had a certain length of time on the network. 

My question is, is there a way to set this up via PHP or possibly a program that is available in the repos that I could install for a client and limit users to a time limit on that network per each day? Then requiring them to aquire a new ip.

---

### Post by Gunman1982 on 2010-04-06
Do you want them to just get a new ip or that they get blocked and have to go pay/request new access?

First part can be easily done by changing the lease time for the ip adresses in the dhcp-server config. 
Can't help you with the second part though.

---

