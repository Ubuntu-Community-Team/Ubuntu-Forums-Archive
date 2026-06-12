---
title: "Defining complex host names"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by kseise on 2010-01-11
I am looking to edit my /etc/hosts file to include a host that uses dynamic DNS.  Since I don't have a static IP address, I have an address like example.ddns.org.  When I enter that in the hosts file and try to ping the machine, I am informed that there is no route to the host.  

Is this possible to setup?  If so, how would I do it?

Thanks,
Kseise

---

### Post by sanderj on 2010-01-11
I think this is not a host name thing, but a routing thing. To check: does pinging your public IP address work?

If not, it's a routing thing. You need to instruct your NAT device how to handle that. My Zyxel apparantly handles it correctly.

BTW: you can solve NAT problems by using IPv6: "sudo apt-get install miredo" will get you there.

---

