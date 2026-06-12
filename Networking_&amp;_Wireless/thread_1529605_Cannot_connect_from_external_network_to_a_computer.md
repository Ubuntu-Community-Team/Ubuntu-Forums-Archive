---
title: "Cannot connect from external network to a computer sitting inside a router"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by psi1978 on 2010-07-12
Hello,

I am trying to connect from outside router to a computer sitting inside a router.
I figured out the WAN ip address of my router through [http://www.who.is/](http://www.who.is/). That ip was "24.xx.xxx.x"
I tried to ping that ip from outside the router and I succeeded it.
And I tried ssh -v "24.xx.xxx.x" and it gave me errors like the following

OpenSSH_4.3p2, OpenSSL 0.9.8e-fips-rhel5 01 Jul 2008
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 24.xx.xxx.x [24.xx.xxx.x] port 22.
debug1: connect to address 24.xx.xxx.x port 22: Connection refused
ssh: connect to host 24.xx.xxx.x port 22: Connection refused

Strange thing is the ip address I got from who.is. is different than the ip address that the router shows me.
The router is Linksys WRT54G and it shows me WAN ip "192.168.123.xxx".

Well, I tried to connect from outside the router with that ip and I failed miserably. I tried to connect to that ip inside the router and I succeeded.
ssh server is running and DMZ setting is correct. I tried to uncheck all the blocking rule of the firewall in the router admin page. I even tried port forwarding, but it doesn't work.

Could you help me a little bit? I am running Ubuntu 10.04
Thank you in advance.

---

### Post by John Bean on 2010-07-12
You need to do a bit of research about "network address translation" (NAT) and "port forwarding" when requiring access to a "local area network" (LAN) from an external "wide area network" (WAN).

Google is your friend.

---

### Post by endotherm on 2010-07-12
well, you are looking for info aobut port forwarding, so check out this site for instructions on how to config your router. 
[http://portforward.com/](http://portforward.com/)


be aware however, that this will just give you access. I would do a good bit of study on locking down your server and your ssh before exposing an remote access port to the web.

---

