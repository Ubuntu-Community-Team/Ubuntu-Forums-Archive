---
title: "Intermittent Internet Connectivity with Intrepid Ibex"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by jkounis on 2008-12-30
I recently upgraded from 7.10 Gutsy Gibbon to 8.10 Intrepid Ibex.

Unfortunately, I am now experiencing intermittent connectivity to the Internet. I will suddenly lose connectivity to the Internet (through a gateway/router) for up to a minute at a time. However, connectivity within the network (192.168.1.x) is still reliable. Other machines on the network are not having this problem, so it is not a router or ISP issue. The problem is isolated to the machine that I upgraded to 8.10.

Here is a sample of what happens when I try to ping google.com. Sometimes it works; sometimes it doesn't. (At the same time I was doing this test, an adjacent machine was continually pinging google.com with no problem).

[INDENT]pgadmin@pgfs:~$ ping google.com
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

pgadmin@pgfs:~$ ping google.com
PING google.com (72.14.205.100) 56(84) bytes of data.
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=1 ttl=240 time=102 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=2 ttl=240 time=100 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=3 ttl=240 time=104 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=4 ttl=240 time=104 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=5 ttl=240 time=103 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=6 ttl=240 time=106 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=7 ttl=240 time=103 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=8 ttl=240 time=101 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=9 ttl=240 time=102 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=10 ttl=240 time=102 ms
^C
--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9035ms
rtt min/avg/max/mdev = 100.305/103.147/106.467/1.723 ms[/INDENT]

The problem also exists with just an IP address, so it's not a DNS issue. Here are the results of some pings to 209.85.171.100 (one of google.com's servers):

[INDENT]pgadmin@pgfs:~$ ping 209.85.171.100
PING 209.85.171.100 (209.85.171.100) 56(84) bytes of data.
^C
--- 209.85.171.100 ping statistics ---
22 packets transmitted, 0 received, 100% packet loss, time 21017ms

pgadmin@pgfs:~$ ping 209.85.171.100
PING 209.85.171.100 (209.85.171.100) 56(84) bytes of data.
64 bytes from 209.85.171.100: icmp_seq=3 ttl=239 time=43.6 ms
64 bytes from 209.85.171.100: icmp_seq=4 ttl=239 time=38.5 ms
64 bytes from 209.85.171.100: icmp_seq=5 ttl=239 time=40.1 ms
64 bytes from 209.85.171.100: icmp_seq=6 ttl=239 time=41.5 ms
64 bytes from 209.85.171.100: icmp_seq=7 ttl=239 time=44.8 ms
64 bytes from 209.85.171.100: icmp_seq=8 ttl=239 time=41.2 ms
^C
--- 209.85.171.100 ping statistics ---
8 packets transmitted, 6 received, 25% packet loss, time 7023ms
rtt min/avg/max/mdev = 38.535/41.656/44.823/2.110 ms
pgadmin@pgfs:~$ ping 209.85.171.100
PING 209.85.171.100 (209.85.171.100) 56(84) bytes of data.
64 bytes from 209.85.171.100: icmp_seq=1 ttl=240 time=44.7 ms
64 bytes from 209.85.171.100: icmp_seq=2 ttl=240 time=40.2 ms
^C
--- 209.85.171.100 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 40.256/42.499/44.742/2.243 ms
pgadmin@pgfs:~$ ping 209.85.171.100
PING 209.85.171.100 (209.85.171.100) 56(84) bytes of data.
64 bytes from 209.85.171.100: icmp_seq=1 ttl=240 time=49.2 ms
64 bytes from 209.85.171.100: icmp_seq=2 ttl=240 time=46.0 ms
64 bytes from 209.85.171.100: icmp_seq=3 ttl=240 time=43.3 ms
^C
--- 209.85.171.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 43.320/46.201/49.245/2.434 ms
[/INDENT]

I am using a static IP. Due to a bug in the GNOME Network Manager (described  [here]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html") and [here]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/"), I edited the network interfaces as follows:

[INDENT]pgadmin@pgfs:/etc$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.4
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.5
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1[/INDENT]

Here is my /etc/resolv.conf:

[INDENT]pgadmin@pgfs:/etc$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 66.215.64.14
nameserver 24.205.1.14
nameserver 24.205.192.61 [/INDENT]

I also tried to disable IPv6, but that didn't help. Here's my /etc/modprobe.d/aliases file:

[INDENT]pgadmin@pgfs:/etc$ grep pf-10 /etc/modprobe.d/aliases 
alias net-pf-10 off
#alias net-pf-10 ipv6[/INDENT]

If this helps, here is my ifconfig:
[INDENT]pgadmin@pgfs:/etc$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:1e:21:4d  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe1e:214d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15608 (15.6 KB)  TX bytes:5419 (5.4 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:15:58:1e:21:4c  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe1e:214c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:220319 (220.3 KB)  TX bytes:60865 (60.8 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101657 (101.6 KB)  TX bytes:101657 (101.6 KB)
[/INDENT]

Here is my lspci | grep Eth:
[INDENT]pgadmin@pgfs:/etc$ lspci | grep Eth
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
[/INDENT]

Here is my route -n

[INDENT]pgadmin@pgfs:/etc$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
[/INDENT]

I don't know if this matters since I'm not using DHCP, but here's my /etc/dhcp3/dhclient.conf: 
[INDENT]pgadmin@pgfs:/etc$ cat /etc/dhcp3/dhclient.conf 
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
pgadmin@pgfs:/etc$ cat /etc/dhcp3/dhclient.conf 
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
[/INDENT]

Any ideas?

---

### Post by jkounis on 2008-12-30
I thought that this additional information would help:

(1) I'm using a Netgear FVS114 VPN Firewall/Router

(2) I learned from previous upgrades not to burn my bridges behind me. So I bought a new hard disk for the 8.10 upgrade, and I kept my old disk with 7.10 on it.

I just inserted the 7.10 disk back into the computer and it's working fine. So it is clearly not a hardware problem or network problem. It seems to be isolated to just this machine when it runs 8.10.

---

### Post by Rohan Kapoor on 2008-12-30
WHen you say upgrade, did you upgrade Ubuntu or just install the new one?

---

### Post by jkounis on 2008-12-31
In answer to the question regarding how I upgraded: I installed a fresh copy of 8.10 onto a blank hard drive. My intention was to copy the /home directory onto the new system from my old hard drive after I had configured the  new system. As it stands, we're still running on 7.10 due to the network connectivity issues.

---

### Post by Rohan Kapoor on 2008-12-31
> **jkounis said:**
> In answer to the question regarding how I upgraded: I installed a fresh copy of 8.10 onto a blank hard drive. My intention was to copy the /home directory onto the new system from my old hard drive after I had configured the  new system. As it stands, we're still running on 7.10 due to the network connectivity issues.
Allright, I see. So you really didn't upgrade what you did was install 8.10.

I believe you said that you were using static ip addresses, in that case, there are some small bugs in 8.10.

Following this guide: [http://ubuntuforums.org/showthread.php?t=1025805](http://ubuntuforums.org/showthread.php?t=1025805) should solve your problems! Let us know if you need more help!

---

### Post by jkounis on 2008-12-31
Thanks. Sorry I wasn't clear in my use of the term "upgrade". 

I had already followed the procedures in the post you recommended. The only difference is that my network is 192.168.1.x instead of 192.168.3.x as described in the post. I included copies of /etc/network/interfaces and /etc/resolv.conf in my original post, and I believe they are correctly configured.

I am making some progress at troubleshooting the problem. Here's what I found. The problem seems to have something to do with DNS:

(1) I re-installed 8.10 on the problem machine and it worked fine with a dynamic IP address assigned by the Netgear FVS114 router via DHCP.

(2) The machine on which I am installing Ubuntu 8.10 used to have an address of 192.168.1.4 and was the primary DNS server on the network. Another machine at 192.168.1.8 is the secondary DNS server. (Of course, I intend to re-install bind9 on the 192.168.1.4 machine as soon as I get Ubuntu 8.10 up and working).

(3) As soon as I follow the recommended procedures to change the Ubuntu machine's address from the dynamically assigned IP address to the static IP address 192.16.1.4, the problems begin to appear. (Maybe because all the machines on the network are looking to 192.168.1.4 to resolve their network addresses?) BTW, the backup server, 192.168.1.8 is still up, and there is no apparent ill effect since all the machines are resolving DNS through the secondary server.

(3) There is something weird going on between the router's DNS settings and general internet connectivity on the Ubuntu 8.10 machine, which I really don't understand. 

The router has a setting for the DNS server addresses that it uses, which it will provide to other machines on the network via DHCP. These _must be the same as_ the DNS servers in the Ubuntu 8.10 machine's /etc/resolv.conf. If they don't match, then the Ubuntu machine cannot connect to anything, even via an IP address . For example, "ping 209.85.171.100" will not work.

I really don't understand why a DNS setting on the router would affect a command such as "ping 209.85.171.100" on the Ubuntu machine. According to everything I learned about networking, DNS isn't required for that command to work.

For example, if I edit /etc/resolv.conf on the Ubuntu 8.10 machine and set the nameservers to  208.67.222.222 & 208.67.220.220 (opendns.com's name servers), and then I connect to the the router and tell it to use the my ISP's DNS servers at 66.215.64.14 &  24.205.1.14, then the Ubuntu 8.10 machine loses _all internet connectivity_, even to straight IP addresses. (Connectivity within the network to 192.168.1.x is not affected). As soon as I connect to the router and change the DNS settings to match the Ubuntu 8.10 machine, the Ubuntu machine regains network connectivity, albeit still somewhat unreliably (frequent dropouts).

Since I have configured /etc/network/interfaces and /etc/resolv.conf to use static IP addresses and static DNS servers and not to use DHCP, I have no idea why the router DNS settings should affect network connectivity on the 8.10 machine, especially when I try to ping to a straight IP address such as 209.85.171.100 (one of google.com's IP addresses).

I'll probably get to the bottom of this in a day or so and will post the results here.

---

### Post by Rohan Kapoor on 2009-01-01
> **jkounis said:**
> Thanks. Sorry I wasn't clear in my use of the term "upgrade". 

I had already followed the procedures in the post you recommended. The only difference is that my network is 192.168.1.x instead of 192.168.3.x as described in the post. I included copies of /etc/network/interfaces and /etc/resolv.conf in my original post, and I believe they are correctly configured.

I am making some progress at troubleshooting the problem. Here's what I found. The problem seems to have something to do with DNS:

(1) I re-installed 8.10 on the problem machine and it worked fine with a dynamic IP address assigned by the Netgear FVS114 router via DHCP.

(2) The machine on which I am installing Ubuntu 8.10 used to have an address of 192.168.1.4 and was the primary DNS server on the network. Another machine at 192.168.1.8 is the secondary DNS server. (Of course, I intend to re-install bind9 on the 192.168.1.4 machine as soon as I get Ubuntu 8.10 up and working).

(3) As soon as I follow the recommended procedures to change the Ubuntu machine's address from the dynamically assigned IP address to the static IP address 192.16.1.4, the problems begin to appear. (Maybe because all the machines on the network are looking to 192.168.1.4 to resolve their network addresses?) BTW, the backup server, 192.168.1.8 is still up, and there is no apparent ill effect since all the machines are resolving DNS through the secondary server.

(3) There is something weird going on between the router's DNS settings and general internet connectivity on the Ubuntu 8.10 machine, which I really don't understand. 

The router has a setting for the DNS server addresses that it uses, which it will provide to other machines on the network via DHCP. These _must be the same as_ the DNS servers in the Ubuntu 8.10 machine's /etc/resolv.conf. If they don't match, then the Ubuntu machine cannot connect to anything, even via an IP address . For example, "ping 209.85.171.100" will not work.

I really don't understand why a DNS setting on the router would affect a command such as "ping 209.85.171.100" on the Ubuntu machine. According to everything I learned about networking, DNS isn't required for that command to work.

For example, if I edit /etc/resolv.conf on the Ubuntu 8.10 machine and set the nameservers to  208.67.222.222 & 208.67.220.220 (opendns.com's name servers), and then I connect to the the router and tell it to use the my ISP's DNS servers at 66.215.64.14 &  24.205.1.14, then the Ubuntu 8.10 machine loses _all internet connectivity_, even to straight IP addresses. (Connectivity within the network to 192.168.1.x is not affected). As soon as I connect to the router and change the DNS settings to match the Ubuntu 8.10 machine, the Ubuntu machine regains network connectivity, albeit still somewhat unreliably (frequent dropouts).

Since I have configured /etc/network/interfaces and /etc/resolv.conf to use static IP addresses and static DNS servers and not to use DHCP, I have no idea why the router DNS settings should affect network connectivity on the 8.10 machine, especially when I try to ping to a straight IP address such as 209.85.171.100 (one of google.com's IP addresses).

I'll probably get to the bottom of this in a day or so and will post the results here.
No problem. We all make mistakes sometimes. No worry's mate!

As a temporary fix, why don't you make Ubuntu and the router's DNS match so that it works.

Unfortunately, I really don't have any other suggestions for you to try, maybe someone else can help1

---

### Post by jkounis on 2009-01-05
Actually, even with the DNS addresses matching, I had 20-30 sec. dropouts every 1-2 minutes, which was unacceptable. What was really weird was that, even during the dropouts, I could connect to the router just fine. I just couldn't get outside the network.

The problem was more involved than I thought. It seemed to be related to the fact tat I had two IP addresses on the same network (a configuration that worked fine in Ubuntu 6 and 7.. but not in 8.10 Intrepid Ibex).

Either disabling one of the adapters, or bonding the two together with the same IP address solved the problem. In the end, I bonded the two using a procedure I found at [http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html]("http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html").

I posted a detailed report of my tests at [http://ubuntuforums.org/showthread.php?t=1031164]("http://ubuntuforums.org/showthread.php?t=1031164") ([SOLVED] Internet Connectivity Problems with Static IPs/2 network adapters).

---

### Post by Rohan Kapoor on 2009-01-05
> **jkounis said:**
> Actually, even with the DNS addresses matching, I had 20-30 sec. dropouts every 1-2 minutes, which was unacceptable. What was really weird was that, even during the dropouts, I could connect to the router just fine. I just couldn't get outside the network.

The problem was more involved than I thought. It seemed to be related to the fact tat I had two IP addresses on the same network (a configuration that worked fine in Ubuntu 6 and 7.. but not in 8.10 Intrepid Ibex).

Either disabling one of the adapters, or bonding the two together with the same IP address solved the problem. In the end, I bonded the two using a procedure I found at [http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html]("http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html").

I posted a detailed report of my tests at [http://ubuntuforums.org/showthread.php?t=1031164]("http://ubuntuforums.org/showthread.php?t=1031164") ([SOLVED] Internet Connectivity Problems with Static IPs/2 network adapters).
Ah allright I see! Glad you could solve it!

---

