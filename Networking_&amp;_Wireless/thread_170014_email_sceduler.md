---
title: "email sceduler"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by harishg on 2006-05-03
I run ubuntu linux on my laptop at home and have to work on windows xp at university.I sometimes have some work running overnight the results of which I would want to automatically be emailed to me.Is there any way to do this or is there some way to make my linux machine at home visible to my windows machine at university.

---

### Post by nanotube on 2006-05-03
well, the easy way to make your linux machine accessible is to install ssh server. 
```
sudo apt-get install openssh-server
```
then you can ssh into your machine from anywhere (assuming that your firewall does not block it, and that you are not behind a NAT router - in which case you have to open port 22, and forward it to your machine through the router)

---

