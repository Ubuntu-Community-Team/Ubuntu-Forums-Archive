---
title: "Can't connect with ubuntu"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by hambos22 on 2009-07-02
Hello! I have ubuntu 8.04. Internet used to worked well but suddenly stoped. On xp is working but on linux not.

I have Atheros AR5007G with the latest madwifi drivers. 
It makes connection with the Wireless but it hasn't internet

---

### Post by upunik on 2009-07-02
I had a very similar problem this morning after the update.
Did you accept an update this morning

My /etc/resolv.conf was empty

Added the following line and all is OK for now
nameserver 192.168.1.1

where 192.168.1.1 is my wireless router

This file should not be edited as it will get overwritten

I am sure we will be advised of the proper fix soon

---

### Post by hambos22 on 2009-07-02
i've done a clean installation

---

### Post by upunik on 2009-07-02
> **hambos22 said:**
> i've done a clean installation

That was quick

---

### Post by hambos22 on 2009-07-02
well i will try it and i post immediatly the results. Thanx

---

### Post by hambos22 on 2009-07-02
no.. it didn;t work

---

### Post by upunik on 2009-07-02
> **hambos22 said:**
> no.. it didn;t work

You say it makes a connection to the wireless

Can you ping the ip address of your wireless router ?
Can you ping 91.189.94.12 ?

---

### Post by hambos22 on 2009-07-02
it makes thw wireless connection but it has no internet...

how can i ping?

ip adress of the router is 192.168.10.254

---

### Post by upunik on 2009-07-02
> **hambos22 said:**
> it makes thw wireless connection but it has no internet...

how can i ping?

ip adress of the router is 192.168.10.254

Quickest way is to open a terminal session and type ping 192.168.10.254

---

### Post by hambos22 on 2009-07-02
well.. i tried ubuntu 9.04.. my wifi driver works out of the box.. the only reason which i had 8.04 was intel driver because 9.04 has bugs with it.. but now i find a guide which solves my prblem with 9.04..

btw thanx my friend for your help

i think tha madwifi drivers had the problem

---

### Post by coen.demilander on 2009-07-02
I have changed PCLOS for Ubutu 9.04 2 weeks ago and could not since then gain access to my mailboxes at Vodacom or iBurst through Evolution or Firefox.  I can also not connect to do Internet banking.  I'm connected to the Internet using Ethernet with a iBurst desktop modem.

---

