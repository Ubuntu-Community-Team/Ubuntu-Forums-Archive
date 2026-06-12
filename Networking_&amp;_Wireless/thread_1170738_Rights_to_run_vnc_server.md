---
title: "Rights to run vnc server ??"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by fld on 2009-05-26
Hi,

I'm exploring the remote assistance possibilities on jaunty.
On the machine "needing assistance" I set up various users. The one usually active (let's call him user A) is not the default user (the one created during installation, user B). 
Now what happens is: if I'm logged in as user A, the vino-preferences window will say I can only connect from localhost. And that's indeed what happens - the connection does not work from my "assisting" machine in the same LAN.
Switching to user B, the window changes saying the machine may be accessed from localhost or it's LAN IP address. 
So...assuming that making the machine accessible from internet is only a matter of adding a port forwarding rule on the router, the goal here would be that of **making user A "accessible" through vnc from LAN**.

ufw says not active. iptables gives ..ko file error so I assume the module is not even loaded. no entries in hosts.allow/deny. 
btw. I don't even get any vino process with ps aux...
the vino-preferences window above looks fine (I can't find a local_only checkbox there which I googled...was that removed?)

any idea...please? :(

bye,
fld

---

