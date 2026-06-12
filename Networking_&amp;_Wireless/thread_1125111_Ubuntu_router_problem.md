---
title: "Ubuntu router problem"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by manosbg on 2009-04-14
Hi!

I've installed Ubuntu 8.10 and I want it to be a server in the office - I know I should install Ubuntu server, but this was easier for me. So I want it to be a router, to share the internet connection through the rest of the office computers, to have a mail server and to host the firm's website. I've been strugling and finally, by using variuos sources I managed to run it as a router. The problem is that all of the office PC's have internet, but the ubuntu itself doesn't! I've been tryin' to figure out what the cause might be but still can't find out. Can you please help me as I've banging my head off the wall for 2 days now?

Thanks in advance!!!

---

### Post by inobe on 2009-04-14
welcome 

what guides did you follow, maybe one of use can offer a suggestion.

also include the hardware on the server, for example the network cards and how they are in connection with the router.

---

### Post by manosbg on 2009-04-14
Frankly I don't know anymore what I have done, as it was waaaaay to much.

I have a static IP on the eth0, from my ISP, in /etc/network/interfaces i have declared that, both the eth0 and eth1.

I've enabled in /etc/sysctl.conf ipv4 forwarding.

I've configured the dhcpd3 server, and in /etc/default/dhcp3-server, I've added both eth0 and eth1 as when it was only on eth0 the server couldn't start. Can that be the problem?

I wrote different kind of iptables commands, and it all seems to work - no matter what I've wrote since it began to route the internet, it routes. And the server itself doesn't have a connection.

I just don't know what to do :(

---

### Post by manosbg on 2009-04-14
Can somebody tell me where I can find a detailed walk-trough for how to set up internet sharing on Ubuntu Server, so both the server and the other computers from the internal network to have Internet? Thanks!

---

### Post by inobe on 2009-04-14
that setup is way beyond the knowledge i have to offer, i did find the actual ubuntu documentation for that.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

