---
title: "best setup for a easily browsable network"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by tigerstripedcat on 2011-04-11
I run one linux machine and a windows machine. I would like to be able to ping my windows machine from the linux machine without using the /etc/hosts file to do it.  I'm sure the host file would work, but I want all computers (I have some laptops too) easily seen on the network without modifying the host files of all the computers, so I assumed that DD-wrt could do a decent job of keeping all hostnames in order.

I tried enabling DNSMasq in dd-wrt but with no success.  All the termology is driving me wild (NetBios, WINS, Master Browser, DNSMasq, etc. etc.). 

Can someone recommend a setup that would fit my needs?  I'd rather use the router to handle all this, but I guess just being able to ping my windows machine without an entry in /etc/hosts would be a big step forward for me.  I had wins (winbind) setup using samba, but I think it was the host file that was doing the resolving (but not totally sure).

Thanks
jack

---

