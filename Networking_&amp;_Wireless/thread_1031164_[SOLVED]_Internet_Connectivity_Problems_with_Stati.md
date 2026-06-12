---
title: "[SOLVED] Internet Connectivity Problems with Static IPs/2 network adapters"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by jkounis on 2009-01-05
I have posted a couple of times about some network issues I have experienced with Ubuntu 8.10 in these two links: [[wired LAN dead/intermittent in 8.10]]("http://ubuntuforums.org/showthread.php?t=1023056") and [[Intermittent Internet Connectivity with Intrepid Ibex]]("http://ubuntuforums.org/showthread.php?t=1025439"). I finally found a workaround, but decided to post the final report of my findings here, in case it helps someone else.

Something has changed between Ubuntu 7.10 and 8.10 in the way traffic is handled when you have two network cards on the same network. The change has resulted in me having unreliable or no Internet connectivity (depending on the router). However, connectivity within my network (192.168.1.x) was not affected.

I have no idea if this warrants a bug report on 8.10 Intrepid Ibex, since I can't figure out enough about the problem to determine it it's a router problem or a software problem.

My configuration is as follows:
> 
SERVER1: LAMP and DNS server running Ubuntu 7.10. 
The server has two gigabit Ethernet adapters on the same network with two different IP addresses. One address hosts is used for the Samba server; the other one hosts Netatalk.

Adapter #1: Broadcom NetXtreme BCM5789 Gigabit Ethernet controller (PCI-Express bus) 
eth0 IP Address: 192.168.1.4
Adapter #2: Broadcom NetXtreme BCM5788 Gigabit Ethernet controller (PCI Bus) 
eth1 IP Address: 192.168.1.5

SERVER2: An _old_, **_old_** server with a 550MHz AMD K6 processor running Ubuntu 6.06 LTS. It's only job is as a secondary DNS server.
IP Address: 192.168.1.8

Firewall/router: Netgear FVS114


I installed a fresh copy of Ubuntu 8.10 on SERVER1. Everything worked fine. However, once I edited /etc/network/interfaces to set a static IP address, SERVER1 had intermittent dropouts connecting to the Internet. Connectivity within the 192.168.1.x network was unaffected, but during the dropouts, it was impossible to even issue "ping 74.125.45.100" (this is one of google.com's IP addresses). Here is a sample run:

> pgadmin@pgfs:~$ ping google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
^C
--- google.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 8999ms

pgadmin@pgfs:~$ ping google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=240 time=42.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=240 time=41.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=240 time=41.4 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=240 time=47.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=240 time=42.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=6 ttl=240 time=50.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=7 ttl=240 time=40.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=8 ttl=240 time=42.6 ms
^C
--- google.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7029ms
rtt min/avg/max/mdev = 40.050/43.567/50.756/3.362 ms
pgadmin@pgfs:~$ ping google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
^C
--- google.com ping statistics ---
20 packets transmitted, 0 received, 100% packet loss, time 19012ms


_**HIGH-LEVEL SUMMARY**_

Something has changed in the way Ubuntu 8.10 handles wired networking with static IPs and two network adapters on the same network. In my case, I had to replace my router to prevent long dropouts. 

Two other routers simply won't work with Ubuntu 8.10, even though they work fine with machines running other versions of Ubuntu, Windows XP, Windows 2000, Windows Vista, Mac OS X, and Mac OS 9.

Here are the results of the tests. Note that in all tests, the rest of the network worked fine, and all other machines on the network had Internet access. 

What is really weird is that, even after I lost all connectivity outside the network, _I could still ping the router and connect to it via its HTTP interface_ (by pointing my browser to [http://192.168.1.1](http://192.168.1.1)) from the Ubuntu 8.10 machine. So I could see the router, and it could see me, but it wouldn't let the Ubuntu 8.10 machine reach the Internet, while at the same time allowing traffic from every other machine on the network through. This occurred on both a Netgear and a DLink router.

I hope this might help someone who encounters a similar problem.

Here are the results of each of the router tests:

Linksys BEFSX41: Works Fine

Netgear FVS114: 30-40 sec dropouts every 1-2 mins on the Ubuntu 8.10 machine. Internet connectivity is completely lost if the DNS settings on the router and the settings on the Ubuntu 8.10 machine are not identical. (Even ping to a straight IP address won't work).

DLink DIR-655: Works fine for 1 min, and then the Ubuntu 8.10 machine loses all Internet connectivity. The only way to regain connectivity is to disable either eth0 or eth1. Then the other adapter works fine.

Here are details about each router test:

_**Linksys BEFSX41 Router**_
    This router works fine. No problems noted.
    Note that [http://ubuntuforums.org/showthread.php?t=1023056]("http://ubuntuforums.org/showthread.php?t=1023056") suggests that loss of internet connectivity is related to an SNMP message that Ubuntu 8.10 sends out. The Linksys router is the only one of the three that supports SNMP. It's also the only one of the three that works. Coincidence?

_**Netgear FVS114**_
(1) Scenario 1:
   eth0 set to 192.168.1.4
   eth1 set to 192.168.1.5
   /etc/resolv.conf pointing to 208.67.222.222 and 208.67.220.220

   Router set to use DNS 208.67.222.222 and 208.67.220.220

RESULT: The internet drops intermittently for 30-60 seconds every minute or two. 

Connectivity within the network 192.168.1.x is unaffected. Other machines on the network are unaffected.

(2) Scenario 2:
   eth0 set to 192.168.1.4
   eth1 set to 192.168.1.5
   /etc/resolv.conf pointing to 208.67.222.222 and 208.67.220.220

   Router set to use my ISP's DNS servers 66.215.64.14 and 24.205.1.14.

RESULT: The internet is _completely inaccessible_ on the Ubuntu 8.10 machine. 

Connectivity within the network 192.168.1.x is unaffected. It is still possible to connect to the router on 192.168.1.1 from the Ubuntu machine, but he router gives no indication why it's not letting traffic through. Other machines on the network are unaffected. 

Note: The DNS server settings on the router and the Ubuntu 8.10 machine must match. Even typing "ping 209.85.171.100" won't work. This is particularly confusing to me, since I didn't think that pinging a straight IP address required DNS to be functioning.

_**DLink DIR-655 Router**_

(1) Scenario 1:

   eth0 set to 192.168.1.4 / gateway 192.168.1.1
   eth1 set to 192.168.1.5 / gateway 192.168.1.1

After a reboot, internet connectivity works for about 60 seconds, then fails entirely. 

There is absolutely _no connectivity_ outside the 192.168.1.x network, even to straight IP addresses. (connectivity within the network is just fine. It's still possible to connect to the router at 192.168.1.1).

Other machines on the network are unaffected.

(2) Scenario 2:

After Internet connectivity is lost in the above scenario, it can be restored by preventing one of the two adapters from accessing the Internet. This can be done by typing:
```
sudo route del -net 0.0.0.0 eth1
```

Internet connectivity is now restored, although there is still 5-9% packet loss pinging google.com, which seems high. (Packet loss on the Netsys router is 0-1%).

To make the change permanent, I commented out the gateway entry for eth1 in /etc/network/interfaces:

```
auto eth1
iface eth1 inet static
address 192.168.1.5
#gateway 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
```

**Update**
I bonded eth0 and eth1 together by following the procedure on [http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html]("http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html"). After configuring bonding as recommended, all problems were solved.

This works fine for me, but I'm still curious. I wonder why I had such problems with two network adapters on the network? I had no problems with Ubuntu 7.10 in the same configuration.

---

