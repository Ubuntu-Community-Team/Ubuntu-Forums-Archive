---
title: "cannot get two computers to connect"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by kainalu on 2008-12-04
Im having an odd problem.

I have three computers in my room 192.168.0.100 , 101 , and 102

the two computers 192.168.0.101 and 102 can talk perfectly and 192.168.0.100 and 101 can talk perfectly but 100 cannot talk to 102.

the following are not right:

attempt to ssh from 102 leads to changed host key error. after deleting ~/.ssh/known_hosts, the server ( 100 ) repeatedly rejects a good password. ssh from 101 works fine.

attempts to get to ( 100 ) from ( 102 ) through mythtv get a database error. ( 101 ) can talk just fine and show tv.

attempts to get to mythweb through 102 fail, but work fine through 101.

i can ping the server fine however from anywhere
there are no firewalls anywhere. 
I have tried resetting the router and the router config checks out fine
it was working last week.


thank you for the help!

---

### Post by Iowan on 2008-12-05
All 3 machines have the same usernames (at least the one you're using)?

---

### Post by kainalu on 2008-12-05
actually no, all three are different

---

### Post by kainalu on 2008-12-15
anybody know what is going on? 

ssh will attempt to connect but rejects my password. the rest simply don't work. still having trouble

---

### Post by Iowan on 2008-12-16
You can log onto that machine locally with the same username/password?

---

### Post by kainalu on 2008-12-18
yes, all works well locally, but remotely:

no ssh
no mythtv
no mysqlserver
no http


weird huh?

---

### Post by The Cog on 2008-12-18
It all makes me wonder if you are talking to the machine you think you are. Just to double-check, I would run **arp -an** and **ifconfig** on each machine, and double-check that each machines arp table contains the correct MAC addresses for the other two machines.

---

### Post by chessmani on 2008-12-27
Are they in the same subnet? How are the computers physically connected?

---

### Post by kainalu on 2009-01-17
it turned out the wireless part of the router somehow gave out 192.168.0.100 to both the laptop and the server. I turned off wireless and it now works fine. thanks for all your help guys

---

