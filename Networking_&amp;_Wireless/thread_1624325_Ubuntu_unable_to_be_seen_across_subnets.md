---
title: "Ubuntu unable to be seen across subnets"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by jsalcido on 2010-11-17
I recently implemented a ubuntu 10.4 LTS  proxy server using squid, clamav-freshclam, dansguardian, and sarg.  I am on a segmented network. The network my server is on has no issues.  It will proxy, content-scan/filter and return webpages.  I have 8 segmented networks in total.  The other 7 are hit and miss.  It works then it won't see the server.  If I run a ping-t from another network it will run for a few then stop responding.  In an attempt to allow traffic I installed firestarter and allowed http, https, and http-alt (8080) traffic from everyone.  It begins to work then stops.  Any help would be greatly appreciated..

Joe Salcido

---

### Post by peyman on 2010-11-17
What are your ip address and subnet masks of your segments? How do you route packets between them?

---

### Post by jsalcido on 2010-11-18
We have a level 3 core switch with both fiber and Ethernet connections.  This switch routes between all 8 segmented subnets. I currently have a CentOS server running basically the same configuration (squidguard instead of dansguardian) and is working just fine.  It is just time for upgrade of the machine, so I decided to go with Ubuntu and DansGuardian this time. 

The network the server sits on is: 10.0.0.0/24
Other networks are:
10.0.2.0/24
10.0.3.0/24
10.0.4.0/24
10.0.5.0/24
10.0.6.0/24
10.0.7.0/24
10.0.8.0/24
10.0.200.0/24
We use static IP addresses for all machines.  Approximately 350.

---

### Post by SeijiSensei on 2010-11-19
I usually place the proxy server just behind the Internet gateway so it's ahead of all the subnets and make it the default gateway for all of them.  Is that not possible for you?

---

### Post by jsalcido on 2010-12-13
The proxy is working flawlessly, when ti doesn't stop traffic.  It accepts a few connections from a particular machine then as if it believed it were being attacked it refuses to answer requests.  Except on its own subnet (10.0.0.0).

---

