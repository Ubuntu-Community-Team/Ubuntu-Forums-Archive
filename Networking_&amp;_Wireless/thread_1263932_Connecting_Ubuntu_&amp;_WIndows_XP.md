---
title: "Connecting Ubuntu &amp; WIndows XP"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2009-09-11
Hi everyone!

I am connecting two computers directly using a crossover ethernet cable. It works perfectly when both are using WIndows XP. When I change to Ubuntu in one of them, it stops working. My ubuntu detects the connection but is unable to get an IP address: when I type ifconfig I get an eth0 entry but without any Ip address.

I am sure that the problem is in the Ubuntu one, since the WIndows XP detects a network but does not receive anything.

Do you know what should I do so that I can make them "talk"??

Thanks

---

### Post by skynet2060 on 2009-09-11
Lookup samba on google or wikipedia. Also make sure you are not using a static ip address on your ubuntu system.

---

### Post by dannyz on 2009-09-11
which machine connects to the internet xp or ubuntu ?

---

### Post by skynet2060 on 2009-09-12
Any machine can connect to the internet. Just plug one of your systems to your router or modem, enable your system to automatically find a IP address and you should be all set.

Personal LOGO: every human can have riches that can go a far length of time, but everlasting riches is knowledge.

---

### Post by skynet2060 on 2009-09-12
for mosquetero,

What I ment was, both machines should not be using dynamic IP addresses. To make two machines communicate with a crossover cable to need to manualy assign IP addresses to both systems.

---

