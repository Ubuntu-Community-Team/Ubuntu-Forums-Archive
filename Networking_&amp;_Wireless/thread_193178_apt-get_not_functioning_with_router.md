---
title: "apt-get not functioning with router"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by racsw on 2006-06-09
Hello,
   If I connect my DSL modem output directly to my PC, apt-get works as it should, upgrades, everything.
   If I connect the DSL Modem to the Netgear router, and plug my PC into the router (normal connection), I get my email and have all web functions, but apt-get fails to work.

Can someone help?   I didn't have this problem with 5.10.

Thanks,
Robert

I am connected right now normally (through the router), and here's the result of my route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Here's my ifconfig results:

eth0      Link encap:Ethernet  HWaddr 00:16:76:24:1B:58
          inet addr:192.168.0.2  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe24:1b58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3367519 (3.2 MiB)  TX bytes:265485 (259.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

---

### Post by nanotube on 2006-06-09
[QUOTE=racsw]Hello,
   If I connect my DSL modem output directly to my PC, apt-get works as it should, upgrades, everything.
   If I connect the DSL Modem to the Netgear router, and plug my PC into the router (normal connection), I get my email and have all web functions, but apt-get fails to work.

Can someone help?   I didn't have this problem with 5.10.

Thanks,
Robert

I am connected right now normally (through the router), and here's the result of my route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Here's my ifconfig results:

eth0      Link encap:Ethernet  HWaddr 00:16:76:24:1B:58
          inet addr:192.168.0.2  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe24:1b58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3367519 (3.2 MiB)  TX bytes:265485 (259.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)[/QUOTE]
that is mighty strange. everything looks like it /should/ work. what is the error output of apt-get? just fails to resolve/connect?

how about trying aptitude instead of apt-get, by the way? aptitude is better all around, maybe it will get around your problem, too.

---

### Post by racsw on 2006-06-09
Thanks for the reply.  Here's the result of "sudo apt-get update"

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

I know absolutely it's the router, as it works perfect connected directly to the modem.  I just don't know and need some help.

Thanks,
Robert

---

### Post by racsw on 2006-06-09
The other reason I need to fix this is because Synaptic won't work for the same reason.  (but it does when connected direct)

Robert

---

### Post by racsw on 2006-06-10
I hope somebody is going to help on this, all I get is more questions :-? 

If I hook directly to my DSL modem, everything works, including apt-get.  When I am connected like this, here is the results of "route -n"

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.101.0.0      0.0.0.0         255.255.192.0   U     0      0        0 eth0
0.0.0.0         70.101.0.1      0.0.0.0         UG    0      0        0 eth0


When I'm connected through my router, my email and browsing works, but apt-get does not.  Here's the results of "route -n" when connected through the router.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

I'm not very good at the networking thing, but it seems to me that if we can tell this system that anytime you want to connect to the outside world (70.101.0.0) your Gateway should be 192.168.0.1.

Then apt-get should know that the route "should" be 192.168.0.1 --> 70.101.0.0.
If someone can tell me how to set this up, we'll see if it works.

Thanks,
Robert

---

### Post by nanotube on 2006-06-10
[QUOTE=racsw]I hope somebody is going to help on this, all I get is more questions :-? 

If I hook directly to my DSL modem, everything works, including apt-get.  When I am connected like this, here is the results of "route -n"

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.101.0.0      0.0.0.0         255.255.192.0   U     0      0        0 eth0
0.0.0.0         70.101.0.1      0.0.0.0         UG    0      0        0 eth0


When I'm connected through my router, my email and browsing works, but apt-get does not.  Here's the results of "route -n" when connected through the router.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

I'm not very good at the networking thing, but it seems to me that if we can tell this system that anytime you want to connect to the outside world (70.101.0.0) your Gateway should be 192.168.0.1.

Then apt-get should know that the route "should" be 192.168.0.1 --> 70.101.0.0.
If someone can tell me how to set this up, we'll see if it works.

Thanks,
Robert[/QUOTE]
your routing tables are perfectly fine. when you are connected to the router, it says that when trying to connect to local net, (192.168.0.0), you don't need any gateway, and when trying to connect to anything else (0.0.0.0), you should go through your router (192.168.0.1). 

so i don't know what is going on here. 
can you try connecting to the package repositories with your browser, and see if that works? just point your firefox to like , security.ubuntu.com, or archive.ubuntu.com, and see if it comes up.

also, like i said earlier, can you try aptitude instead of apt-get, and see if that works?
```
sudo aptitude update
```

you should also try to see if maybe somehow your apt-get got configured to use some kind of proxy or something weird like that. check the conf files in directory /etc/apt/apt.conf.d/ and see if there is anything about proxies or networking that looks weird. (or you can just post the content of all the files in that directory to this thread and we can take a look - they are all small 3-5line files).

---

### Post by RRS on 2006-06-10
Just an Idea.........
Do the repositories normally use any particular ports?

I've never had a reason to check into this but perhaps something in the routers firewall configuration is blocking synaptic and/or the repositories.

Seems a possibility worth checking into.

---

### Post by nanotube on 2006-06-11
[QUOTE=RRS]Just an Idea.........
Do the repositories normally use any particular ports?

I've never had a reason to check into this but perhaps something in the routers firewall configuration is blocking synaptic and/or the repositories.

Seems a possibility worth checking into.[/QUOTE]
i think it all goes through the standard port 80...

---

### Post by racsw on 2006-06-11
OK, first, thank you for not dropping this.

Here's the results:

1.  FireFox can access both repositories perfectly, no problem.

2.  I tried "aptitude", same exact response.

3.  I see no references to a Proxy in any of those files.  But as you asked, here are those files:

05aptitude:
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$";

99update-notifier:
DPkg::Post-Invoke {"if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";};

10periodic:
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "1";

20archive:
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";

70debconf:
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};

50unattended-upgrades:
// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu dapper-security";
//	"Ubuntu dapper-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//	"vim";
};

I am assuming that because my browser can access the repositories, there is no router problem, but to go further, I tried your "sudo aptitude update" again to get the IP address of the failed accesses.  Here's a few: 

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]

So I pinged 85.133.25.8, and it pinged fine.  I am also assuming that the "80" on the end is some reference to Port 80, but I don't know.

That's everything I think you asked for for now.

Here's some info from my Netgear Router:


Connection Time 	01:45:34
Connection Method 	DynamicIP
IP Address 	70.101.52.221
Network Mask 	255.255.192.0
Default Gateway 	70.101.0.1
Lease Obtain	SUN JUN 11 09:11:35 2006
Lease Expire	MON JUN 12 03:11:35 2006

WAN Port
MAC Address 	00:0f:b5:a0:c7:93
IP Address 	70.101.52.221
DHCP 	DHCPClient
IP Subnet Mask 	255.255.192.0
Domain Name Server
	66.133.170.2
	67.50.135.146
 
LAN Port
MAC Address 	00:0f:b5:a0:c7:92
IP Address 	192.168.0.1
DHCP 	ON
IP Subnet Mask 	255.255.255.0


Thanks,
Robert

---

### Post by nanotube on 2006-06-12
well... i am sorry to say, but at this point i'm stumped.
if your browser can access the repositories, but your apt-get cannot, i do not know where else to look. your conf files do not appear to have anything funky about proxies or anything, your apt does attempt to connect to the right ip at the right port... i just don't know where else to look. 

unlikely, but maybe in the firewall... what's the output of
```
sudo iptables --list -v
```

---

### Post by ns2048 on 2006-06-12
Can you try disabling IPV6 support and trying again? Add 'blacklist ipv6' to '/etc/modprobe.d/blacklist', and reboot your system.
--ns2048

---

### Post by black bear theory on 2006-06-12
[QUOTE=ns2048]Can you try disabling IPV6 support and trying again? Add 'blacklist ipv6' to '/etc/modprobe.d/blacklist', and reboot your system.
--ns2048[/QUOTE]

i have been following along with this thread - i'm having the same problems - and blacklisting ipv6 doesn't appear to help as far as ftp connections.

bbt

[edit to add: my problem turned out to be a bad /etc/apt/location file]

---

### Post by thermal on 2006-06-12
ns2048 - I tried disbling the ipv6 as you suggested.
I have the same issue as racsw, but am connected to an ADSL modem/router in one through a small switch.
5.10 works without issues.
FC5 works without issues.
Web browsing, ping, etc. all work in everything.
apt-get, synaptic and aptitude all fail in exactly the same way as racsw.
Question:
What has changed between 5.10 and 6.06 to stop apt-get?
Thanks very much to anyone who has any clues on this.
Any lurkers out there, please jump on the thread so we can get a better picture :)

---

### Post by zasf on 2006-06-12
What's in your /etc/resolv.conf?

I guess there is only your router IP address, put your DNS servers like this

```
$cat /etc/resolv.conf
domain yyyy #if any
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
nameserver 192.168.0.1

```

and it will work

---

### Post by jvictor on 2006-06-12
I'd suggest using the ISPs DNS server addresses instead of your Router, bcoz there are some 'bad boy' routers that dont do the job of a DNS server perfectly ,  they might have been 'tuned' (pronounced as perverted) by the vendors to support the 'lion-share' operating system.

---

### Post by nanotube on 2006-06-12
[QUOTE=black bear theory]
[edit to add: my problem turned out to be a bad /etc/apt/location file][/QUOTE]
i dont even have a /etc/apt/location file. (but i am running breezy, so maybe dapper is supposed to have it...)

---

### Post by nanotube on 2006-06-12
[QUOTE=jvictor]I'd suggest using the ISPs DNS server addresses instead of your Router, bcoz there are some 'bad boy' routers that dont do the job of a DNS server perfectly ,  they might have been 'tuned' (pronounced as perverted) by the vendors to support the 'lion-share' operating system.[/QUOTE]
well, according to his error output, the dns has been resolved properly, and the ip address of repository servers shows up... but i guess it doesn't hurt to try...

---

### Post by racsw on 2006-06-12
Hi,
  Here's the result:

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

One other fellow asked what was in my /etc/resolv.conf file:

nameserver 192.168.0.1

One line, that's all.

I know I'm "Networking Challenged", there is no doubt ;-)
But I thought that if we can fool apt-get into thinking it's connected to the actual DSL modem (where it does work), maybe by altering a configuration file somewhere, or perhaps listing the entire route through the router to the DSL Modem, something like that?  Just for testing?

I appreciate your efforts and help on this.

Regards,
Robert

---

### Post by zasf on 2006-06-12
jvictor and I are saying the same thing. Some routers don't work very well in some circumstances (like apt-get or w3m, these is what I found), don't ask me why, but I resolved your very same issue by indicating in /etc/resolv.conf not only my router as nameserver but also my ISP's ones.

Check your router web configuration page, when connected it should list your ISP given DNS servers and put them in /etc/resolv.conf ;)

---

### Post by racsw on 2006-06-12
I did add my IP DNS addresses to the /etc/resolv.conf file as such:

domain frontiernet.net
nameserver 66.133.170.2
nameserver 67.50.135.146
nameserver 192.168.0.1

Then I did "sudo /etc/init.d/networking restart"
Here's what happened:

* Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:24:1b:58
Sending on   LPF/eth0/00:16:76:24:1b:58
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:24:1b:58
Sending on   LPF/eth0/00:16:76:24:1b:58
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.2 -- renewal in 33220 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

Then, I did another "cat /etc/resolv.conf", and here's what I got:

domain frontiernet.net
nameserver 192.168.0.1

I did this twice, same results.  Restarting the network deletes those two DNS addresses for some reason.

Hope this helps.
Robert

---

### Post by racsw on 2006-06-12
...and here's the router status:

IP Address 70.101.52.221
DHCP 	DHCPClient
IP Subnet Mask 	255.255.192.0
Domain Name Server
	66.133.170.2
	67.50.135.146

---

### Post by Slim Odds on 2006-06-12
[quote=jvictor]I'd suggest using the ISPs DNS server addresses instead of your Router, bcoz there are some 'bad boy' routers that dont do the job of a DNS server perfectly ,  they might have been 'tuned' (pronounced as perverted) by the vendors to support the 'lion-share' operating system.[/quote] 
This is ridiculous. Please tell me how you think the router knows the difference between Windows IP traffic and Linux IP traffic (clue: it doesn't).

Most routers are actually designed to ***work***. What a surprise!

If you are using a NAT/Firewall router for access to an ADSL or cable Internet connection, the router will pick up the DNS addresses from the ISP. The router will then transparently provide DNS forwarding from it's own address (typically 192.168.X.1).

Unless you have an actual faulty piece of hardware (slightly unlikely), this method works just fine. When your client (Linux or Windows, it doesn't matter) makes a request to the router for a DNS resolution, you **are** using your ISP's specified DNS servers.

---

### Post by nanotube on 2006-06-12
[QUOTE=Slim Odds]This is ridiculous. Please tell me how you think the router knows the difference between Windows IP traffic and Linux IP traffic (clue: it doesn't).

Most routers are actually designed to ***work***. What a surprise!
[/QUOTE]
well, good thing you said "most" :) i had (still have sitting somewhere) a netgear "travel router", and i just can't get it to do dns passthrough, so i have to go and manually set the isp dns servers. buncha threads online complain of the same. this is of course true on both win and lin, so has no bearing directly on this question, but your statement just reminded me of that one :)

---

### Post by nanotube on 2006-06-12
[QUOTE=racsw]
domain frontiernet.net
nameserver 192.168.0.1

I did this twice, same results.  Restarting the network deletes those two DNS addresses for some reason.

Hope this helps.
Robert[/QUOTE]
well, this is no surprise - when you do network restart, it re-requests all the dhcp info, so your dns server info is also refreshed. since the router just sends itself as dns server, of course, your resolv.conf gets overwritten. if you want to use those isp dns servers directly, just edit resolv.conf (and might as well delete the router entry for good measure), but do NOT do the network restart. 

now, not that it should make any difference, but hey, when you are out of ideas, it doesn't hurt to try.

---

### Post by zixxer on 2006-06-12
i had the same problem..this seems to be solved by going right to the backbone...im behind a linksys rt41p2 voip router. it must be something with how the routers are passing NAT or something....any ideas? ill keep pecking away at this

EDIT: could it possibly be how the repos are handling the traffic? most likely not..but i still cant figure out whats goin on...ill keep watching ethereal

---

### Post by black bear theory on 2006-06-12
[QUOTE=nanotube]i dont even have a /etc/apt/location file. (but i am running breezy, so maybe dapper is supposed to have it...)[/QUOTE]

oops! it's /etc/apt/sources.list!

basically i changed any mention (only the uncommented lines) of us.archive.ubuntu.com to archive.ubuntu.com and all ftp:// to http:// and everything worked!

a bit cryptic but it should make more sense if you look at the file.

hth bbt

---

### Post by Sauli on 2006-06-13
I have a similar problem and it has been discussed in an other thread [http://ubuntuforums.org/showthread.php?p=1131794#post1131794](http://ubuntuforums.org/showthread.php?p=1131794#post1131794). No solution to my case yet.

I am connected to Internet via ADSL modem/router. All other Internet traffic seems to work ok. I can also access the synaptic repositories with my browser.

As zasf suggested, I added my ISP nameserver lines to my /etc/resolv.conf file.
sauli@Subuntu:/etc$ cat resolv.conf
nameserver 193.229.0.40
nameserver 193.229.0.42
nameserver 192.168.0.254
It did not help.  I still get the 'Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)' messages from synaptic.

---

### Post by jvictor on 2006-06-13
> This is ridiculous. Please tell me how you think the router knows the difference between Windows IP traffic and Linux IP traffic (clue: it doesn't).

Most routers are actually designed to work. What a surprise!

If you are using a NAT/Firewall router for access to an ADSL or cable Internet connection, the router will pick up the DNS addresses from the ISP. The router will then transparently provide DNS forwarding from it's own address (typically 192.168.X.1).

Unless you have an actual faulty piece of hardware (slightly unlikely), this method works just fine. When your client (Linux or Windows, it doesn't matter) makes a request to the router for a DNS resolution, you are using your ISP's specified DNS servers.

Oh yeah ?! It didnt work that way for me, what ur talking is **theory** but things dont work always that way. 
Please try to understand the values of the community before posting what comes to ur mind. Slinging may look good on slackware or debian forum, but here its a different ball game. Welcome to the 'community'

---

### Post by zasf on 2006-06-13
[QUOTE=Sauli]I have a similar problem and it has been discussed in an other thread [http://ubuntuforums.org/showthread.php?p=1131794#post1131794](http://ubuntuforums.org/showthread.php?p=1131794#post1131794). No solution to my case yet.

I am connected to Internet via ADSL modem/router. All other Internet traffic seems to work ok. I can also access the synaptic repositories with my browser.

As zasf suggested, I added my ISP nameserver lines to my /etc/resolv.conf file.
sauli@Subuntu:/etc$ cat resolv.conf
nameserver 193.229.0.40
nameserver 193.229.0.42
nameserver 192.168.0.254[/QUOTE]

I had this issue with breezy and Router D-Link G604T, browsing the internet was fine but apt-get and gaim failed (does your gaim work?)

I found out that both apt-get and gaim could not resolve address via 192.168.1.1, so I added my ISP DNS server to /etc/resolv.conf and it worked (both apt-get and gaim). I actually haven't had this problem with dapper (same configuration) since I use the same resolv.conf from breezy and local static ip (no dhcp, thus /etc/resolv.conf is not overwritten)

> It did not help.  I still get the 'Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)' messages from synaptic.

why localhost?? try apt-get from terminal

and one more test. Open a fresh terminal, check if apt-get works for example doing "sudo apt-get update", then try to do "w3m [http://archive.ubuntu.com](http://archive.ubuntu.com) -4". It should open a text broswer and display the webpage, use Ctrl+C to exit, then run "sudo apt-get update" again.

---

### Post by zasf on 2006-06-13
[QUOTE=Slim Odds]This is ridiculous. Please tell me how you think the router knows the difference between Windows IP traffic and Linux IP traffic (clue: it doesn't).

Most routers are actually designed to ***work***. What a surprise!

If you are using a NAT/Firewall router for access to an ADSL or cable Internet connection, the router will pick up the DNS addresses from the ISP. The router will then transparently provide DNS forwarding from it's own address (typically 192.168.X.1).

Unless you have an actual faulty piece of hardware (slightly unlikely), this method works just fine. When your client (Linux or Windows, it doesn't matter) makes a request to the router for a DNS resolution, you **are** using your ISP's specified DNS servers.[/QUOTE]

I don't know if it's linux or window fault, but this is actually a problem that I also faced. It would be good to investigate further so that we could either file a bug if that is the case.

---

### Post by zasf on 2006-06-13
[QUOTE=nanotube][QUOTE=racsw]
domain frontiernet.net
nameserver 192.168.0.1

I did this twice, same results. Restarting the network deletes those two DNS addresses for some reason.

Hope this helps.
Robert[/QUOTE]

well, this is no surprise - when you do network restart, it re-requests all the dhcp info, so your dns server info is also refreshed. since the router just sends itself as dns server, of course, your resolv.conf gets overwritten. if you want to use those isp dns servers directly, just edit resolv.conf (and might as well delete the router entry for good measure), but do NOT do the network restart. 

now, not that it should make any difference, but hey, when you are out of ideas, it doesn't hurt to try.[/QUOTE]

try setting your computer to static IP and put your DNS servers (you can do it all from the GUI - System | Administration | Networking). Static IP should be enough not to overwrite /etc/resolv.conf.

I also heard some other friends having a similar problem with Dapper, they found out that some network scripts were broken in /etc/dhcp3, you might want to search the forum.

---

### Post by Sauli on 2006-06-13
[QUOTE=zasf]I had this issue with breezy and Router D-Link G604T, browsing the internet was fine but apt-get and gaim failed (does your gaim work?)

I found out that both apt-get and gaim could not resolve address via 192.168.1.1, so I added my ISP DNS server to /etc/resolv.conf and it worked (both apt-get and gaim). I actually haven't had this problem with dapper (same configuration) since I use the same resolv.conf from breezy and local static ip (no dhcp, thus /etc/resolv.conf is not overwritten)



why localhost?? try apt-get from terminal

and one more test. Open a fresh terminal, check if apt-get works for example doing "sudo apt-get update", then try to do "w3m [http://archive.ubuntu.com](http://archive.ubuntu.com) -4". It should open a text broswer and display the webpage, use Ctrl+C to exit, then run "sudo apt-get update" again.[/QUOTE]

Thanks for trying to help. I appreciate it. Unfortunately there is still no breaktrough in solving the problem.

This is what I got from a fresh terminal:
sauli@Subuntu:/etc$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) dapper Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://fi.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://fi.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

sauli@Subuntu:/etc$ w3m [http://archive.ubuntu.com](http://archive.ubuntu.com) -4
w3m: Can't load [http://archive.ubuntu.com](http://archive.ubuntu.com).

Accessing site [http://archive.ubuntu.com](http://archive.ubuntu.com) by entering the address in Firefox works fine though. Also gaim seems to work.

This may be silly, but you know, when you can't find the problem you start suspecting also things that by common knowledge shouldn't have anything to do with the problem. Anyway, you mentioned D-Link router and I also do have a D-Link wireless router DI-624 in my network. It routes the wireless laptop traffic to the same ADSL modem/router as this Ubuntu PC, which has the problem.  I have not changed settings in DI-624 and I have no other specific reasons to suspect it. But do my problem symptoms imply that I may have misconfigured also the fixed traffic, dns queries or something to route via that box?

---

### Post by zasf on 2006-06-13
does 'ping fi.archive.ubuntu.com' work? I remember that it didn't work from terminal before I did the resolv.conf trick

---

### Post by Sauli on 2006-06-13
[QUOTE=zasf]does 'ping fi.archive.ubuntu.com' work? I remember that it didn't work from terminal before I did the resolv.conf trick[/QUOTE]

Yes pinging works:
sauli@Subuntu:~$ ping fi.archive.ubuntu.com
PING fi.archive.ubuntu.com (85.133.25.8) 56(84) bytes of data.
64 bytes from 85.133.25.8: icmp_seq=1 ttl=51 time=51.3 ms
64 bytes from 85.133.25.8: icmp_seq=2 ttl=51 time=51.2 ms
64 bytes from 85.133.25.8: icmp_seq=3 ttl=51 time=51.0 ms
64 bytes from 85.133.25.8: icmp_seq=4 ttl=51 time=51.5 ms
64 bytes from 85.133.25.8: icmp_seq=5 ttl=51 time=51.2 ms
64 bytes from 85.133.25.8: icmp_seq=6 ttl=51 time=50.6 ms
64 bytes from 85.133.25.8: icmp_seq=7 ttl=51 time=50.9 ms

--- fi.archive.ubuntu.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 9191ms
rtt min/avg/max/mdev = 50.625/51.134/51.531/0.367 ms

I also tried modifying the /etc/dhcp3/ dhclient.conf 
'prepend domain-name-servers' line as suggested by eboo in [http://ubuntuforums.org/showthread.php?t=187466&highlight=%2Fetc%2Fdhcp3](http://ubuntuforums.org/showthread.php?t=187466&highlight=%2Fetc%2Fdhcp3)
but with no avail.

---

### Post by zasf on 2006-06-13
[QUOTE=Sauli]Yes pinging works:
sauli@Subuntu:~$ ping fi.archive.ubuntu.com
PING fi.archive.ubuntu.com (85.133.25.8) 56(84) bytes of data.
64 bytes from 85.133.25.8: icmp_seq=1 ttl=51 time=51.3 ms
64 bytes from 85.133.25.8: icmp_seq=2 ttl=51 time=51.2 ms
64 bytes from 85.133.25.8: icmp_seq=3 ttl=51 time=51.0 ms
64 bytes from 85.133.25.8: icmp_seq=4 ttl=51 time=51.5 ms
64 bytes from 85.133.25.8: icmp_seq=5 ttl=51 time=51.2 ms
64 bytes from 85.133.25.8: icmp_seq=6 ttl=51 time=50.6 ms
64 bytes from 85.133.25.8: icmp_seq=7 ttl=51 time=50.9 ms

--- fi.archive.ubuntu.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 9191ms
rtt min/avg/max/mdev = 50.625/51.134/51.531/0.367 ms[/QUOTE]

hum.. so your problem is different to the one I had

> I also tried modifying the /etc/dhcp3/ dhclient.conf 
'prepend domain-name-servers' line as suggested by eboo in [http://ubuntuforums.org/showthread.php?t=187466&highlight=%2Fetc%2Fdhcp3](http://ubuntuforums.org/showthread.php?t=187466&highlight=%2Fetc%2Fdhcp3)
but with no avail.

watch out, the file is different, see [http://ubuntuforums.org/showpost.php?p=1095240&postcount=3](http://ubuntuforums.org/showpost.php?p=1095240&postcount=3). But manually adding dns nameserver should do the job at least until ip renowal..

---

### Post by Slim Odds on 2006-06-13
[quote=jvictor]Oh yeah ?! It didnt work that way for me, what ur talking is **theory** but things dont work always that way. 
Please try to understand the values of the community before posting what comes to ur mind. Slinging may look good on slackware or debian forum, but here its a different ball game. Welcome to the 'community'[/quote]  I'm not "slinging", wise-guy. What I mentioned is not a "**theory**", it's a **fact**. I have a router that *works* and I know for a fact that this is how most vendors designed their units.

So please climb down off of your high horse and take it easy.  Sometimes these network issues are hard to figure out, but what I see most of the time in these forums is people jumping to conclusions. Mostly wrong conclusions. I'm trying to be a voice of reason and give some help based on lots of experience with IP networks.

---

### Post by jvictor on 2006-06-13
[QUOTE=racsw]I did add my IP DNS addresses to the /etc/resolv.conf file as such:

domain frontiernet.net
nameserver 66.133.170.2
nameserver 67.50.135.146
nameserver 192.168.0.1

Then I did "sudo /etc/init.d/networking restart"
Here's what happened:

* Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:24:1b:58
Sending on   LPF/eth0/00:16:76:24:1b:58
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:24:1b:58
Sending on   LPF/eth0/00:16:76:24:1b:58
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.2 -- renewal in 33220 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

Then, I did another "cat /etc/resolv.conf", and here's what I got:

domain frontiernet.net
nameserver 192.168.0.1

I did this twice, same results.  Restarting the network deletes those two DNS addresses for some reason.

Hope this helps.
Robert[/QUOTE]

As long as u use DHCP it will get overwritten , u need to install a tool called resolvconf for that

---

### Post by jvictor on 2006-06-13
> So please climb down off of your high horse and take it easy. LOL !! :razz: 

as though it matters !

---

### Post by racsw on 2006-06-13
The saga continues...;-)

Ok, based on the advice, I changed the Netgear FVS318 Router setup to static IP and static DNS addresses.  When I did this, the router rebooted.  Without doing anything else, my email and all web functions continued to operate fine.

I rebooted Umbutu, then looked at my /etc/resolv.conf, the result of which is:

search frontiernet.net
nameserver 66.133.170.2
nameserver 67.50.135.146

All my email and web functions still worked fine, so I did my oft-repeated (lately)
"sudo apt-get update", and I got the exact same "No connection..." results as I have posted earlier, exactly.

The thread has accumulated a lot of folks, but I think this is what I was supposed to try.  No luck so far.

Robert

---

### Post by Slim Odds on 2006-06-13
[quote=racsw]
All my email and web functions still worked fine, so I did my oft-repeated (lately)
"sudo apt-get update", and I got the exact same "No connection..." results as I have posted earlier, exactly.

The thread has accumulated a lot of folks, but I think this is what I was supposed to try.  No luck so far.

Robert[/quote] 
Since most of your networking is working, try using ethereal to see what's going wrong.

---

### Post by ZTiger on 2006-06-14
I ran into this same problem. I was noticing a post in [another thread]("http://www.ubuntuforums.org/showthread.php?t=190679") with similar issues and tried modifying my apt.conf file.
I took the "Acquire::http::Proxy "false"; out of the /etc/apt.conf file and now I don't have any problems getting through my netgear router.

It might be worth a shot for you.

---

### Post by gadgetgirl on 2006-06-15
Awesome, thanks ZTiger, that fixed it for me.

---

### Post by Sauli on 2006-06-15
My problem was solved. The key was to notice an unwanted proxy setting at System -> Preferences -> Network Proxy.

See my message at [http://ubuntuforums.org/showthread.php?p=1140337#post1140337](http://ubuntuforums.org/showthread.php?p=1140337#post1140337)

Sauli

---

### Post by zasf on 2006-06-15
[QUOTE=zasf][QUOTE=sauli]It did not help. I still get the 'Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)' messages from synaptic.[/QUOTE]

why localhost?? try apt-get from terminal[/QUOTE]

that's why, it was a proxy related problem.

Nice to know you solved it.

---

### Post by racsw on 2006-06-15
Bingo!!
It's all working now!
My sincere thanks to you, ZTiger.:D 

Regards,
Robert

---

### Post by nanotube on 2006-06-15
[QUOTE=ZTiger]I ran into this same problem. I was noticing a post in [another thread]("http://www.ubuntuforums.org/showthread.php?t=190679") with similar issues and tried modifying my apt.conf file.
I took the "Acquire::http::Proxy "false"; out of the /etc/apt.conf file and now I don't have any problems getting through my netgear router.

It might be worth a shot for you.[/QUOTE]
interesting, i dont even *have* a /etc/apt.conf file. :)

---

### Post by luften on 2006-06-19
[QUOTE=ZTiger]I ran into this same problem. I was noticing a post in [another thread]("http://www.ubuntuforums.org/showthread.php?t=190679") with similar issues and tried modifying my apt.conf file.
I took the "Acquire::http::Proxy "false"; out of the /etc/apt.conf file and now I don't have any problems getting through my netgear router.

It might be worth a shot for you.[/QUOTE]

Thanks, same thing worked for me. I just installed the latest Ubuntu, and apt-get was not working through my linksys wrt54g router. However, renaming the file 'apt.conf' fixed it :)

---

### Post by m_pav on 2006-06-26
I have been researching this issue for a few weeks now, because my system has had troubles on and off for some time now, the best part of this year and I need to get to the bottom of it.

It appears to be all related to hardware, not software, though there could be some issues with drivers in some setups. Routers and LAN cards with DHCP are failing all over the place but only when using apt or ftp, all other internet connectivity has full functionality. How can I be so sure? I have a laptop and I do some house or place of business calls fixing up peoples problems (those poor people, they all run windows and 90% of them have viruses - shame they chose the lesser, because I always show them Linux). Many of them have broadband, so I can just plug in to their modems and with their permission, test apt and ftp, so I have in a sense, access to a broad variety of testing stations.

My laptop will not connect to apt while I am at home or work unless I change the dns server in my networking setup to use a dns server outside of my LAN, instead of the modems built in dns server (identical modems) but apt almost never fails when I connect to a different brand or model of modem, so I believe it's related to hardware, not the sources.list or /etc/network/interfaces or the apt.conf files. I can remove my expensive modem and stick in a cheap modem and apt works without changing a single file on my system, same broadband account, default settings all round. I have spent hours trying so many settings including disabling all firewalls in both my laptop and my modem, resetting everything to default many times in the process but still apt would not connect, but put in an el-cheapo modem and it works.

If you are having this problem, contact your modem manufacturer and ask them to fix it with a firmware upgrade. In the meantime, change your settings to use an external dns server like 4.2.2.1 & 4.2.2.2 each time you want to run apt of ftp, but be aware that as your modems lease times out, the dns server will be reset to whatever it was in the first place. Your download will stop, so re-open your network configuration screen, re-type the dns servers and apply the changes, then continue with the download. 

Most modem manufacturers that use Linux as their base systems MUST support the same base as what they use, so if they say they don't support Linux, ask them what system their modems run, and if they use a variant of Linux, ask to talk with their highest level manager, and camp on his/her doorstep until it's fixed.

[http://ubuntuforums.org/showthread.php?p=1182547#post1182547](http://ubuntuforums.org/showthread.php?p=1182547#post1182547)

Mike P

---

