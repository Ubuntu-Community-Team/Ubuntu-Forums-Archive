---
title: "router internet access"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by skidz on 2009-03-08
Hi all,

I am setting up a router running Ubuntu 8.10
I used the following sites as tutorials:
[http://howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Right now, I am just in testing, seeing if I can even it do it (new to linux all together)

My network setup right now is... 
Internet -> My old dlink router -> Ubuntu router -> switch -> my computer

I think I have it all set up and working correctly (dhcp is giving out addresses, I can do nslookups), but my computer can't access the Internet. 

If ping [www.google.com](www.google.com) it resolves the IP, but it can't reach the IP.

Is this because I am behind 2 routers now? Like I said before I am in test phase now, and don't want to replace my dlink router tell I am sure it all works great.

Any ideas would be great, and remember, new to linux/unix/ubuntu :)

PS
* the ubuntu router can access the internet.
* firewall is off right now on the ubuntu router
* dlink local network is 192.168.1.X and ubuntu's is 192.168.0.X

---

### Post by skidz on 2009-03-08
Anyone have any ideas?

---

### Post by Iowan on 2009-03-08
> **skidz said:**
> If ping [www.google.com](www.google.com) it resolves the IP, but it can't reach the IP.

Is this because I am behind 2 routers now? Certainly no expert, but it would seem plausible that the routing tables in the two routers might need to be adjusted to pass traffic.

---

### Post by skidz on 2009-03-08
Thx Iowan... 

Like you I am no expert :)... but was kinda thinking the same thing. I have tried to figure it out on my own, but can't find any info on it... Would it be the dlink router that has to have some kind of adjustment on it to pass the traffic on to the ubuntu router? If so, I can't find anything in the dlink that would allow this :)... oh well.. I will most likely just get it as good as I can... then just change the router and test it then...

---

### Post by Iowan on 2009-03-08
Getting further out of my league... you *might* configure the Dlink to port forward (everything???) to the Ubuntu router, but I'd be inclined to remove the Dlink for a trial.  There'd be a lot less "putting back" if that setup didn't work.  If it DID work, then you could start playing with other settings.  
I prefer to keep a working configuration available to reload/reconnect, if my new configuration doesn't work.  Keep in mind that I'm outta my league - and even I don't much trust my advice in this area...

---

