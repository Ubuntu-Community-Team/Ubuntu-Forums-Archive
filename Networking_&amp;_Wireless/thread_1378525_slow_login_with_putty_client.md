---
title: "slow login with putty client"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by fernando_aug on 2010-01-11
Hi all,

This is my first post. In fact I've been reading the forum as guest since I started to use Ubuntu (Jully 2009) and now that the need to post has arrived I've decided to oficially register :).

Well, I've been having issues to connect hrough ssh to a Ubuntu server 9.04 (kernel 2.6.29.4) from a putty client. I runned tests with four clients, two were a Ubuntu desktop 9.04, these two connect normally to the server, the other are two windows xp using putty to connect to the server. 
The problem arise with the windows based machines. On the first login it takes around a minute for the login to be prompted, after that It runs really fast (as they are in local network). If I close the session and try to login again then it runs fast, it prompts for login fast a go on. If I wait some time then the one minute waiting comes again.

I alredy set UseDNS to no, included -u0 option in /etc/default/ssh, seted GSSApiAuthentication to no, and spend a day gooogling for some solution but just got nothing.

Someone can give any clue? 
[]s

---

