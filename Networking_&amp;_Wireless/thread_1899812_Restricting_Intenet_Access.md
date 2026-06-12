---
title: "Restricting Intenet Access"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by achuth on 2011-12-24
Sir,
Suppose I have 50 computers networked using a switch. 
I have installed ubuntu 11.10 in all machines.
One of the computer is connected to the router and has the internet connection.
I would like to restrict internet access to a few computers in the network that I choose.
How can I do this in ubuntu? Please give me some step by step guide on this.

---

### Post by Lars Noodén on 2011-12-24
Do you have Ubuntu on the switch?  What kind of restriction did you have in mind?

---

### Post by achuth on 2011-12-24
Oh. That I don't know. 
Forget about switch.
Suppose I have 10 networked PCs.
Since I have internet connection in one of the computers, it is available in all other computers.
I would like to disable internet connection in 5 PCs even though they are still connected to the network.

---

### Post by Lars Noodén on 2011-12-24
Then I would look at using IPTables on those machines to block all traffic that is to or from anything except the LAN.  Use the [REJECT](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject) target instead of DROP.  That will speed up responses and facilitate diagnosis of any mistakes.

---

