---
title: "same /etc/host for whole network"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by tollboy on 2009-03-18
I have four computer in my network(all on linux). and each is having diffrent name
sys1....sys4. all networking is done.
i want to access each computer from its name.
for e.g ping sys1    (remote request from sys2)

for this i have to do a entry in /etc/hosts file for sys1.

and if i want to do the same from sys3, i have toedit the same file on sys3.

so for accessing by name there should be a entry of other three computer in /etc/host file of a comp.
and if i add a other comp in network with name sys5 i have to edit /etc/hosts file of all four systems and for new 5th one also.




Is this neesary to all the time.
is there any way so i can use the information stored in a single /etc/hosts file which act as a server for others..


I dont know how we to do this with DNS. is there any way????

---

### Post by capscrew on 2009-03-18
> **tollboy said:**
> ...so for accessing by name there should be a entry of other three computer in /etc/host file of a comp.
and if i add a other comp in network with name sys5 i have to edit /etc/hosts file of all four systems and for new 5th one also.


Is this neesary to all the time.

Yes.  You are resolving all hostnames to their IP addreses. 
> 
is there any way so i can use the information stored in a single /etc/hosts file which act as a server for others..

Yes there is.  It's called DNSmasq.  You can read about it [[COLOR="SeaGreen"]**here**[/COLOR]]("http://www.thekelleys.org.uk/dnsmasq/doc.html").  This uses a single /etc/hosts file as the data store.
> 

I dont know how we to do this with DNS. is there any way????

Are you asking about DNS servers?  If so, there is BIND9.

---

### Post by Iowan on 2009-03-20
DNSmasq should be able to serve as both local (caching) DNS server AND DHCP server... installing it is still on my to-do list.

---

