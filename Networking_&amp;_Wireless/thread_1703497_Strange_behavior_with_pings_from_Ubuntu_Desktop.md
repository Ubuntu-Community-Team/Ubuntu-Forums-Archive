---
title: "Strange behavior with pings from Ubuntu Desktop"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by Smigh on 2011-03-09
I've been trying to use MySQL in Ubuntu but I've been having some connection issues and in trying to troubleshoot that, I observed this strange behavior with pings in Ubuntu Desktops inside our network.

- All Ubuntu Servers we have (10.10 and 8.04) behave as expected
- All Windows machines behave as expected
- All 5 Ubuntu Desktops we have, (10.10 and 9.10) exhibit the following unexpected behavior:

If they have a local ip addresses and are connected within the internal network, either to a switch or directly to a router, pings take much longer to be sent. It's not a higher lag, it's the time between each ping that increases. I have to wait for around 5 seconds for each ping, but the time in the ping reply is less than 100ms, also they're all in order so I assume it's the system delaying the sending of each ping.

If I plug a USB 3G modem directly then it works as expected again (~1 sec between each ping sent).

Is this an intended feature, that depends on the network environment, or is this something I should look into more closely?

---

### Post by Smigh on 2011-03-09
I came across a similar issue at [http://ubuntuforums.org/showthread.php?t=820756]("http://ubuntuforums.org/showthread.php?t=820756")

In that case it seemed to be a name resolution problem and using "ping -n" made it work correctly. I tried that and it also works for me. Also, if I ping google's ip directly, it all works fine too (I was pinging the host "www.google.com"). 

So I guess this is some name resolution issue, still, this doesn't make sense: 1) all other OS's besides Ubuntu Desktop, work fine (including Ubuntu Server); 2) every single ping is slowed down, I thought the name resolution came first and it shouldn't interfere with the actual pings after the system got the ip address

This doesn't seem critical as it doesn't affect internet browsing, my only doubt is if this is in someway related with my MySQL problems. Tell me if you have any idea of what's going on.

---

