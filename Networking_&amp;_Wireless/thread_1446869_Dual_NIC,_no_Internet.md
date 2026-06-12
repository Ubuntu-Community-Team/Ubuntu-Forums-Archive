---
title: "Dual NIC, no Internet"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by zap1989 on 2010-04-04
Hey, so I have a dual NIC card I set up on my Dell server.  

One network is for an external dedicated ISP (Acanac).  The other is for local private network (which, also has an internet connection).

I have the external line set up on eth0, and the LAN network on eth1.  I can connect to the server on both...using the external connection (via SSH, APACHE, etc...it is a webserver).  I can also connect via the LAN while on the internal network.

However, when on the server itself, it can't connect to the internet.  I've tried via Firefox, "wget", update manager, software manager, etc...nothing will let me connect.  But I KNOW it has internet, because I can SSH in from outside!  I have tried changing FF settings, but I know it's not FF because it doesn't work via any other method either.

On my /etc/network/interfaces file, I have them both set up as STATIC, with only the external (eth0) having a Gateway.


Any and all ideas are appreciated!  I've been at this for weeks, with no ideas left. :(

---

### Post by RyanRahl on 2010-04-04
can you connect to the internet if one or the other of the interfaces is disabled? What is in your /etc/networking/interfaces file? What kind of services have you tried to use from the server? it seems odd that you can connect to services that use TCP and require a reply so there has to be back and fourth communication. What is your gateway setup like?

---

### Post by Iowan on 2010-04-04
What are the results of **route -n**? Have you tried pinging Internet by IP address? (If that works, check contents of */etc/resolv.conf*.)

---

### Post by zap1989 on 2010-04-04
> **RyanRahl said:**
> can you connect to the internet if one or the other of the interfaces is disabled? 

Yes


> **RyanRahl said:**
> What is in your /etc/networking/interfaces file?

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
    address 192.168.0.179
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    dns-nameservers 67.55.0.11

auto eth0
iface eth0 inet static
    address 192.168.254.1
    network 192.168.254.0
    netmask 255.255.255.0
    gateway 192.168.254.254
    broadcast 192.168.254.255
    mtu 1492
    dns-nameservers 67.55.0.11

> **RyanRahl said:**
> What kind of services  have you tried to use from the server?

Synpatics package manger, the ubuntu gui update manager, wget, apt get install [or whatever], firefox, etc, etc..


> **Iowan said:**
> What are the results of **route -n**? 


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.254.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.254.254 0.0.0.0         UG    100    0        0 eth0


> **Iowan said:**
> Have you  tried pinging Internet by IP address? 

Yes, I can ping.

 ping 66.249.91.104 -c 3
PING 66.249.91.104 (66.249.91.104) 56(84) bytes of data.
64 bytes from 66.249.91.104: icmp_seq=1 ttl=55 time=37.9 ms
64 bytes from 66.249.91.104: icmp_seq=2 ttl=55 time=36.0 ms
64 bytes from 66.249.91.104: icmp_seq=3 ttl=55 time=34.3 ms

--- 66.249.91.104 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 34.302/36.089/37.958/1.509 ms



> **Iowan said:**
> (If that works, check contents of */etc/resolv.conf*.)

nameserver 67.55.0.11
nameserver 66.49.220.95


(I have put this info into resolv.conf myself.  It is the two nameservers of my dedicated external line, Acanac)

---

### Post by RyanRahl on 2010-04-05
I would try a different DNS server just to see what happens. especially if you're geting ping responses from an ip. try putting the IP of a website into the URL bar of your browser and see what happens. This just screams name resolution problem.

have you tried using the gateway on the first interface on the list? You may want to try setting up eth0 as the NIC connected physically to the gateway and only have the gateway defined on this one (as you do already). You want to put it first on the list. Try this: 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
 iface eth0 inet static
     address 192.168.254.1
     network 192.168.254.0
     netmask 255.255.255.0
     gateway 192.168.254.254
     broadcast 192.168.254.255
     mtu 1492
     dns-nameservers 67.55.0.11

auto eth1
iface eth1 inet static
    address 192.168.0.179
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    dns-nameservers 67.55.0.11

sounds crazy but I'm not near a dual nic machine (not in the office) to test whether the order of interfaces in the file makes a difference, i just get the feeling it may.

---

### Post by zap1989 on 2010-04-05
> **RyanRahl said:**
> sounds crazy but I'm not near a dual nic machine (not in the office) to test whether the order of interfaces in the file makes a difference, i just get the feeling it may.

It was originally that way, and I changed it to the way it is now to see if it did help...made no difference.  But when I'm back at the server tonight, I'll try again anyway.


> **RyanRahl said:**
> I would try a different DNS server just to see what happens. especially  if you're geting ping responses from an ip. try putting the IP of a  website into the URL bar of your browser and see what happens. This just  screams name resolution problem.

No, even trying to connect via IP doesn't work.  I can only ping it.  But I can also ping domain names (ie pinging google.ca vs 66.249.91.104 makes no difference, they both work)

---

### Post by RyanRahl on 2010-04-05
> **zap1989 said:**
> 
No, even trying to connect via IP doesn't work.  I can only ping it.  But I can also ping domain names (ie pinging google.ca vs 66.249.91.104 makes no difference, they both work)

wow. that's really strange. have you tried to run a port scan locally and remotely to see if it returns services on one side of the NIC but not the other? Maybe a traceroute from the server will show you where your data is trying to go and where it stops.

---

### Post by zap1989 on 2010-04-05
> **RyanRahl said:**
> have you tried to run a port scan locally and remotely to see if it returns services on one side of the NIC but not the other? Maybe a traceroute from the server will show you where your data is trying to go and where it stops.

how would I go about doing that?

---

### Post by RyanRahl on 2010-04-05
download Angry IP Scanner from here: [http://www.angryip.org/w/Home](http://www.angryip.org/w/Home)
then scan all your interfaces including loopback from the server, from the internet and from the LAN and then check for discrepancies in what services are available and from where.

for traceroute:

open a terminal and enter:
1. sudo apt-get install traceroute (to install the packages you need)
2. traceroute domain or IP
For further information enter man traceroute.

use traceroute from your server to the LAN or the internet. it will show you what router hops you are making and im sure it will show you where your request has stopped (most likely locally) so you can see if your routing is wrong. BTW do you have NetworkManager enabled?

---

### Post by zap1989 on 2010-04-06
Ok, so problem solved...but WEIRDEST thing ever, I think anyway...


So, what it was...I decided trying random things on the modem/router itself.  It turns out, that a set of Port-Forwards I had was screwing it up.  I had  a large range of ports (several thousand), forwarded to the server.  When I Disable this, it works fine.  Which to me, doesn't make any sense...because realistically, shouldn't you be able to forward EVERY port to a machine and it still work?  It'd be like not using a router at all...bah.   And mind you, there's only the one machine connected to this modem/router..and all ports forwarded to the one machine.

Thanks for the help guys!

---

