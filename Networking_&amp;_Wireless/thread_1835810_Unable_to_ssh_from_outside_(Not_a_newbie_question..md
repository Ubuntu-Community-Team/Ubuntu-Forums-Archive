---
title: "Unable to ssh from outside (Not a newbie question.  This is really wierd)"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by manipremkumar@gmail.com on 2011-08-30
I have this very wierd situation.  I have a ubuntu 10.04 server, with two Network cards, configured with two IP's in the same subnet.  SSH is listening on both the IPs., and I am able to ssh into this box from within the lan, using both the IP.
I have a netgear N700 router.  I have forwarded the port to one IP.  I can log in to this box from outside a few times.  But after approximately around 4 hours, it locks me out.  I cannot login.  Then, I change the port forward to route to the 2nd IP.  now, I can connect again, for sometime.  After a few hours, i am again locked out.  This cycle goes around.  
Also, once it happened, i hit crtl C to cancel a login attempt, and i was locked out of both the IP for 4 hours or so.  
I have no clue what is going on.  Any help would be great.  Thanks.

---

### Post by lkjoel on 2011-08-30
On the computer you are using from the outside, are you sure that it is always connected to your network, and not to another network?

---

### Post by manipremkumar@gmail.com on 2011-08-30
I dont understand your question.  I am using my laptop to connect to the server.  When i am in the office, I am in the local network, and i can connect without any problem.  The problem is when I am outside (home), and try to connect through the public static IP.  The router has this IP, and I have set the port forward properly.  I can connect randomly.

---

### Post by Wayne_V on 2011-08-30
when you are in the office you are probably on the same subnet as both NIC's in your pc so you can talk to either without going thru the router.   Having two NICs in one computer on the same subnet will often drive a router batty.   If you really need redundancy, you should set up a load balanced or failover config between this pc and the router (a bond interface for example).

---

