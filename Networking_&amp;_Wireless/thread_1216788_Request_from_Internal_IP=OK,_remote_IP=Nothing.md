---
title: "Request from Internal IP=OK, remote IP=Nothing"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by VyReN on 2009-07-18
Fresh install of Ubuntu Server Edition - Router is port-forwarded correctly (Have also put this machine in the DMZ with the exact same results).  Router IS port-forwarding correctly to another machine.

From the local terminal, the following works:
wget localhost
wget 192.168.0.xxx (local IP)

The following does not:
wget 206.xxx.xxx.xxx (static IP)
wget good.domainname.com

From a remote machine on same network:
192.168.0.xxx = good reply (Web)
good.domainname.com = timeout

Here is where it gets interesting -- I have moved Apache2 to port 8088 (To ensure it wasn't something up with the ISP, also adjusted port-forwarding).
From the local terminal:
wget good.domainname.com = Connection refused (As it should)
wget good.domainname.com:8088 = Timeout
wget 192.168.0.xxx = Connection refused (As it should)
wget 192.168.0.xxx:8088 = Good

This tells me the port forwarding is working (Same result when in the DMZ, btw) but SOMETHING is blocking connections from the outside world to this machine.

This is the 2nd computer I've attempted this setup with and had the same results both times.

Same results with FTP and SSH.  Just peachy locally, zilch remotely (or just when using the remote IP).

Ping (ping good.domainname.com) responds correctly (And it is the machine sending the pong, router is setup to ignore ping requests, no reply when the machine is off).

Totally fresh install, iptables is set to accept across the board, IP address is correct and domain is setup correctly...machine is connected directly to the router, router has all "firewall" type junk turned off (Port forwards to another machine perfectly)...what the 'H' am I missing here?

Thanks
Glen

---

### Post by The Cog on 2009-07-19
Two thoughts:

Does your server have a default route pointing back towards the router? Use the command route to see.

Are you trying to connect to your public address from inside your own network, or from some other site? It will not work from inside your own network because the NAT translation won't work right. You really have to test it from somewhere else on the internet.

---

### Post by VyReN on 2009-07-19
> **The Cog said:**
> Two thoughts:

Does your server have a default route pointing back towards the router? Use the command route to see.

Are you trying to connect to your public address from inside your own network, or from some other site? It will not work from inside your own network because the NAT translation won't work right. You really have to test it from somewhere else on the internet.

*facepalm*

Yep, you nailed it.  5 days I've been tinkering with this....

Thanks!!
-Glen

---

