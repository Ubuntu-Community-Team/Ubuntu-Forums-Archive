---
title: "no route to host when using ssh"
date: 2012-09-30
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2012-09-30
I have a very basic home network with four nodes (let's call then A,B,C and D)

A is the mail server and has a firewall. I can get to A from B and C via ssh, but when I try this from D, I get a 'no route to host' error.

All nodes ares are configured the same and are on the same subnet (192.168.1.x)

I connect from all nodes to A with the IP address; so no DNS issue I guess

I can get to the internet (i.e. browse) from all nodes including D without any problems.

"$> route" looks the same on all nodes
"$> ifconfig" shows the same on all nodes (apart from the ip address)

somewhat at a loss as to what I'm issing

---

### Post by 2F4U on 2012-09-30
- What Linux versions are on the different machines?
- Can you ping A from D?
- Is the firewall configured to allow only particular IP addresses to connect?
- Do all machines use the same connection type, e.g. wireless or wired?

---

### Post by lister171254 on 2012-09-30
sorry, should gave included this in the first place

all machines run the same (latest) version of Ubuntu, they are all wired, the firewall allows 192.168.1.0/24

One thing that doesn't work at all from D to any machine one the local network is ping; they are all unreachable

only thing that's reachable is the router; hence I can get out to the internet. so it looks like only the local network is affected

---

### Post by lister171254 on 2012-09-30
just to clarify.

I pinged C (has no firewall) from B and get a response, but when I do the same from D, I get the network unreachable

Also, most of these machines are connected via a netcomm powerline adapter.

ran nmap with the following result
---------------
Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-10-01 15:03 EST
Nmap scan report for Router1 (192.168.1.1)
Host is up (0.011s latency).
MAC Address: 58:6D:8F:B8:92:E1 (Unknown)
Nmap scan report for 192.168.1.3
Host is up (0.011s latency).
MAC Address: 14:DA:E9:C8:C6:82 (Unknown)
Nmap scan report for GaragePc.zudiewiener.com (192.168.1.6)
Host is up.

-----------------

.1 is the router, which I can get to ok
.3 is A
.6 is D

No sign of B or D; anything above .100 is DHCP

I've done an nmap on C and it sees the router and A,B , but not D


I've also swapped the Netcoom adapters around to eliminate this as a possible cause; same result. D is dead to the rest of the LAN and vice versa

---

### Post by lister171254 on 2012-10-01
Given that D (.6) can see the router (.1) and A (.3) I ran nmap on A with the following result
---------------
Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-10-01 15:47 EST
Nmap scan report for Router1 (192.168.1.1)
Host is up (0.00063s latency).
Nmap scan report for LeosLinux.zudiewiener.com (192.168.1.3)
Host is up (0.00048s latency).
Nmap scan report for MusicPC (192.168.1.5)
Host is up (0.0051s latency).
Nmap scan report for GaragePC (192.168.1.6)
Host is up (0.0100s latency).
Nmap scan report for 192.168.1.10
Host is up (0.0072s latency).
Nmap scan report for 192.168.1.103
Host is up (0.078s latency).
Nmap scan report for 192.168.1.107
Host is up (0.072s latency).
Nmap scan report for 192.168.1.109
Host is up (0.11s latency).
Nmap done: 256 IP addresses (8 hosts up) scanned in 22.89 seconds

---------------

So the question is now why A and D can see each other, A can see everything, but B and C cannot see D

---

### Post by 2F4U on 2012-10-01
Well, at least that answers the original question about ssh, since  without a working ping, ssh is not working either. I think the problems  are burried somewhere in the network topology. What I find interesting  is that the network latency differs much between the hosts, .6 and  .103-.109 are considerably slower than the rest.
What I don't  completely understand is that in your first post you say that there are 4  hosts, but the nmap reports finds 8 hosts. I am wondering what the .1xx  hosts are.

> Also, most of these machines are connected via a netcomm powerline adapter.

Can  you give more information about this, i.e. which machine is connected  through these adapters? I don't know anything about netcomm adapters,  but I am using Devolo PowerLine adapters myself. The Devolo adapters  allow to setup their own encryption mechanism and therefore could form  their own encrypted subnet. Could this be the cause of the problems?

---

### Post by lister171254 on 2012-10-01
The other hosts are phones and tablets. DHCP hosts are .100+

The only permanent addresses are
.1 the router
.3
.5
.6
.10

---

