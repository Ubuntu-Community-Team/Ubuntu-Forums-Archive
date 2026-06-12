---
title: "iptables and postrouting"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by bercy on 2013-01-15
Hi,

My knowledge in networking is very minimal, so I hope that I'll give pertinent information for this question.

I rent a dedicated server from a company called OVH.  This is a french company, with subsidiaries all over Europe.  Basically, when you rent a server from them, by default, you end up with a French IP.

They offer different options on their dedicated servers, one of which is the possibility to add failover IPs for countries of your choice.  Usually, this would be used to help rank your web site higher in search results.

I use the failover IPs for a totally different reason : to be able to access some web sites which do not allow visitors from specific countries.  An example would be some TV web sites in the US not allowing you to watch videos unless you have a US IP address.

One particular web site that I need to access does not allow visitors from France.  So, I ordered a failover IP located in the UK, made some config changes to /etc/network/interfaces, rebooted, and voila, I could access said web site.

For reasons that I will not go into, I needed to use a different IP.  I ordered a new failover IP, reconfigured everything, rebooted, and to my surprise, the web site rejected my access.

I ran a "whois <IP> | grep country" to make sure I did get a UK IP, and the response was indeed "GB", or Great Britain.  This is the same response I got with the original failover IP.  In fact, comparing the output of whois for both IPs only differed in lines where the IPs were mentionned, everything else in the whois records was the same.

Now, the config changes involve iptables (obviously to you expert readers!).  More specifically, I have a line like this :

-A POSTROUTING -o eth0 -j SNAT --to-source <failover IP>

followed by 

post-up /sbin/ifconfig eth0:0 <failover IP> netmask 255.255.255.255 broadcast <failover IP>


Remembering that I still have "access" to both failover IPs, my question is this : is there a way to configure the server so that all outgoing requests will use one IP, EXCEPT FOR ONE PARTICULAR DESTINATION ADDRESS (the web site in question), which would use the other IP, all on the same eth0 interface ?

And more generically, could this be extended to multiple exceptions, using multiple alternate failover IPs ?

Thanks.

---

