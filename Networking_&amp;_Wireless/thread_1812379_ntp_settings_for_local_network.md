---
title: "ntp settings for local network"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by rozo on 2011-07-26
Hi all,

I have a small local network with 2 PC's with ubuntu, the network is disconnected from internet. I want one of them to be the local time server and the other one to synchronize time with it. 
My /etc/ntp.conf on the time server:

server 127.0.0.1

/etc/ntp.conf on the client:

server 192.168.0.4
driftfile /etc/ntp.drift

I can ping the server from the client.
First of all if I run ntpdate from the client it returns "no server suitable for synchronization ...".
Of course after I started ntpd on the time server and the client the latter didn't synchronize time. But if I now connect the server to internet and add a public time server to the ntp.conf it starts working.
What is wrong in this offline configuration? I can't find any information about how to set ntp network when it's not connected to the internet.

---

### Post by rozo on 2011-07-27
Ok, I found the solution here:
[http://fixunix.com/slackware/338104-how-sync-time-lan-ntp.html](http://fixunix.com/slackware/338104-how-sync-time-lan-ntp.html)

---

