---
title: "DNS not resolving properly on 11.04 server"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by pshear0 on 2011-10-11
Hi, Would be very grateful for any assistance you could provide on a DNS problem. I have recently changed my 8.04 server for a newly built 11.04 server

I have a NAT server between my ISP and my local systems. All works well and local systems can talk to the outside world. Outside world can talk to my web server and ssh into my NAT server. The domain address [www.s*****n.com](www.s*****n.com), the NAT server, is in the ISPs DNS.

To ease local administration I implemented DHCP on the NAT server. All works.
I also implemented DNS locally for a domain s*****n.local, all works fine on the local systems that are able to resolve and reverse resolve addresses from both the NAT server and from the www.

The problem is however on the NAT server. If I use nslookup, dig or host it supplies the correct local address from the local dns e.g
[INDENT]*peter@NAT:~$ host connie.s*****n.local*
*connie.s*****n.local has address 192.168.1.2*
[/INDENT]
and when I reverse lookup it works too e.g
[INDENT]*peter@NAT:~$ host 192.168.1.2*
*2.1.168.192.in-addr.arpa domain name pointer connie.s*****n.local.*
[/INDENT]
BUT when I try to ssh I get an error e.g
[INDENT]*peter@NAT:~$ ssh connie.s*****n.local*
*ssh: Could not resolve hostname connie.s*****n.local: Name or service not known*
[/INDENT]
If I try and ping I get the same problem e.g
[INDENT]*peter@NAT:~$ ping connie.s*****n.local*
*ping: unknown host connie.s*****n.local*
[/INDENT]
If this was not working on the local systems, I would think it was a config problem in the reverse dns db BUT it works on the local systems just not on the NAT server. Other things such as looking up fixed addresses by canonical names don't work in the DHCP server and it gives a ip address rather than a resolved name for the last login in the MOTD when I ssh into my NAT server.

My /etc/resolv.conf is:
[INDENT]*domain s*****n.com*
*nameserver 192.168.1.1*
*nameserver 8.8.8.8*
[/INDENT]
My /etc/nsswitch.conf is:
[INDENT]*passwd:         compat*
*group:          compat*
*shadow:         compat*

*hosts:         files mdns4_minimal [NOTFOUND=return] dns mdns4 mdns*
*# hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4*
*networks:       files*

*protocols:      db files*
*services:       db files*
*ethers:         db files*
*rpc:            db files*

*netgroup:       nis*
[/INDENT]Sorry for the long email but trying to give as much info as possible.

Thanks in advance

Peter

---

### Post by newbie-user on 2011-10-11
Don't know if it makes a difference, but my /etc/resolv.conf is like this;

search mydomain.org
nameserver [local dns ip]
nameserver [isp dns]


Otherwise, you could add a list of hosts to the /etc/hosts file.

---

### Post by pshear0 on 2011-10-12
Thanks for the thoughts newbie-user but I am looking to fix dns.

Ok, I seem to have solved it but I'm not sure why. I changed the order of the hosts line in nsswitch.conf to look at dns first e.g.

was - [I]hosts:         files mdns4_minimal [NOTFOUND=return] dns mdns4 mdns
[/I]now -* hosts: dns **        files mdns4_minimal [NOTFOUND=return] *[I]mdns4 mdns
[/I]
All my local devices are Apple devices, could mdns have been messing with dns? Assume looking up 192.168.1.2 and expecting connie.s*****n.local from dns but was being returned connie.local mdns perhaps?Now correctly returns connie.s*****n.local
I'm also having issues with netatalk, I'm thinking the two may be connected*. I*s there a tool for returning what nsswitch resolves?Any thoughts gratefully received.

Regards

Peter

---

### Post by jonobr on 2011-10-12
Interesting post,

I think your logic is correct given the order change then
something before dns was cuasing it.

Given my curious nature, I would swap them round til I found the culprit

---

### Post by Sergius14 on 2011-10-12
I never configured a DNS Server on Ubuntu, but is very common to do this kind of DNS mix, primary for local queries and secondary for external domains. While I believe that is wrong, I have to admit that I never did a full evaluation to the following experience.

I think that a "Domain not found" is valid, good and a positive reply from a DNS server. So, if primary DNS server has successfully replied that that domain doesn't exits, why bother asking to the secondary?

It would very different if primary doesn't reply at all. So, if primary DNS timed out, it would be necessary to ask to the secondary (and so on).


On Windows which I believe that on Ubuntu has to be more of the same, to avoid this issue, on DNS servers, I configure at the interfaces level (over Network Manager) (/etc/resolv.conf, etc.) to use only internal server. Could be localhost (127.0.0.1) for primary and the secondary my internal secondary DNS (if you have). If not, rely only on himself as localhost. This is at the DNS Server as a Client role.

AND the most important, over the DNS Service Console (as Server role), I configure that all external domain queries has to being forwarded to (list of...) N servers (8.8.8.8 or your ISP's).


In this case, all the network (including the DNS Server as a Client) uses my own internal DNS which forwards non-local domains to external DNS Servers.


I know that many ppl use this DNS mix (local/external) and seams to "works" but I never did on them a full test. But on Windows is kinda different, because NetBIOS used to confuse many weekend administrators.


Give it a try.

---

