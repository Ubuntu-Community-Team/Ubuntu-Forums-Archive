---
title: "Two nic cards but no port forwarding."
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by MerlinGuy on 2010-07-06
Hello,

I have two nic cards installed in a Lucid LTS server.  

eth0 is static using
address 192.168.0.235 
gateway 192.168.0.1
netmask 255.255.255.0

and 

eth1 is static using
address 192.168.3.235 
gateway 192.168.3.1
netmask 255.255.255.0

I have my Qwest DSL modem port forwarding port 80 to 192.168.3.235 however this doesn't seem to work if I have both cards running.  If I remove the second card (eth1) and reconfigure eth0 to use 192.168.3.235 I can port forward into my webserver.  

Any ideas?  Can I use port forwarding with two nics on two subdomains?

thanks

---

### Post by MerlinGuy on 2010-07-06
My apologies, I should have read through more posts instead of relying on search that didn't find the answer.  The solution was on this post [Two Static Networks, Dual NIC's, works then down]("http://ubuntuforums.org/showthread.php?t=812222")

Basically I should only set up a gateway on one interface.

Hope this helps others.

---

