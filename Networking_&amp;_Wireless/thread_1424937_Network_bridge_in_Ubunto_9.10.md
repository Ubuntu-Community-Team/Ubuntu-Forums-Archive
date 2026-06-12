---
title: "Network bridge in Ubunto 9.10"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by HugoMA on 2010-03-08
Hello,

I have been searching  for a week now for a solution for my problem.

City hall has a wireless connection available to the public. Since I live close by I thought about using it at home and for that I set up an old machine to run Ubuntu 9.10 desktop and use a Asus Wireless AP WL-330 as an adapter that connects to eth0. That part was easy.
Since I have (so far) 3 other computers (1 PIII w2k, 1 netbook w7 and an Athlon with Caixa Magica 12 Linux) I was thinking using Ubuntu to distribute the internet to the other computers.
eth0 is configured for dynamic IP (192.168.1.xxx) and I was thinking of setting eth1 in the ubuntu machine as 192.168.2.1 and set it up as dhcp server for the rest of the machines (192.168.2.xxx).
Since I only have 1 scree 1 mouse and 1 keyboard I was only able to test what I was getting searching several forums (including this one) in the netbook and it wasn't working.


Today was the 3rd time I instaled Ubuntu (twice last week) so I wanted to get it right this time.


Thanks in advance

---

### Post by sparky-steve on 2010-03-08
> **HugoMA said:**
> ....and for that I set up an old machine to run Ubuntu 9.10 desktop and use a Asus Wireless AP WL-330 as an adapter that connects to eth0. That part was easy.

I presume, as it was easy, that this computer (the router) can connect to the internet and browse OK?

shorewall, amongst others, is a good way of sharing your internet.

```
sudo apt-get install shorewall
```

It takes me just a few minutes to set it up but if you've not done it before, you'll probably need assistance. Post back.

SS

---

### Post by HugoMA on 2010-03-08
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package shorewall is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  shorewall-common
E: Package shorewall has no installation candidate
Hugo@BlackBox:~$ sudo apt-get install shorewall-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  shorewall-doc
The following NEW packages will be installed:
  shorewall-common
0 upgraded, 1 newly installed, 0 to remove and 98 not upgraded.
Need to get 221kB of archives.
After this operation, 1,253kB of additional disk space will be used.
Get:1 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) karmic/main shorewall-common 4.2.10-1 [221kB]
Fetched 221kB in 1s (143kB/s)            
Preconfiguring packages ...
Selecting previously deselected package shorewall-common.
(Reading database ... 128698 files and directories currently installed.)
Unpacking shorewall-common (from .../shorewall-common_4.2.10-1_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up shorewall-common (4.2.10-1) ...


I installed like you said.

I checked synaptic and there's shorewall packages all 4.2.10-1, but only shorewall-shell has the ubuntu Icon. Do I install this one?

---

### Post by sparky-steve on 2010-03-08
Hi

It's changed a little since I originally installed it; But I can confirm that I have shorewall-shell and shorewall-common installed. Additionally, you'll need a few config files.

To sort that, you'll need to know what interface your "internet" connection is on (ie eth0) and the interface that your "LAN" is on (ie eth1 / wlan0 etc)

SS

---

### Post by sparky-steve on 2010-03-08
The config files:

in /etc/default/shorewall, change

```
startup=0
```

to

```
startup=1
```

for the rest of these configs, I will assume your INTERNET is on eth0 and the LAN is on eth1 - you must change them to suit else it wont work!

**/etc/shorewall/interfaces**

```
#
# Shorewall version 4 - Interfaces File
#
# For information about entries in this file, type "man shorewall-interfaces"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-interfaces.html
#
###############################################################################
#ZONE	INTERFACE	BROADCAST	OPTIONS
net eth0 detect routefilter,tcpflags,nosmurfs
lan eth1 detect tcpflags
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

**/etc/shorewall/policy**

```
#
# Shorewall version 4 - Policy File
#
# For information about entries in this file, type "man shorewall-policy"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-policy.html
#
###############################################################################
#SOURCE		DEST		POLICY		LOG		LIMIT:BURST
#						LEVEL
fw 	net 	ACCEPT
lan	net	ACCEPT
lan	lan	ACCEPT
lan	fw	ACCEPT
fw	lan	ACCEPT
net 	all	DROP		info
all	all	REJECT		info
#LAST LINE -- DO NOT REMOVE
```

in /etc/shorewall/shorewall.conf change

```
STARTUP_ENABLED=No
```

to

```
STARTUP_ENABLED=Yes
```

/etc/shorewall/zones

```
#
# Shorewall version 4 - Zones File
#
# For information about this file, type "man shorewall-zones"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-zones.html
#
###############################################################################
#ZONE	TYPE		OPTIONS		IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
net ipv4
lan ipv4
#LAST LINE - ADD YOUR ENTRIES ABOVE THIS ONE - DO NOT REMOVE
```

and finally (for now) /etc/shorewall/rules

```
#
# Shorewall version 4 - Rules File
#
# For information on the settings in this file, type "man shorewall-rules"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-rules.html
#
############################################################################################################################
#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/	MARK
#							PORT	PORT(S)		DEST		LIMIT		GROUP
#SECTION ESTABLISHED
#SECTION RELATED
SECTION NEW
#
#your rules go here#
#
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

In theory, and if memory serves correctly, you should be set to go.

```
sudo shorewall start
```

should get it up and running.

Of course, you either need to set up fixed IP addresses on your LAN, or set up a DHCP server on your "router" machine.

Hope this helps get you on the right track. 

SS

---

### Post by HugoMA on 2010-03-09
I tried connecting, but it didn't work. I'm thinking cause there's no DHCP server.

This is how I want it set up.

public wireless -> asus adapter -> eth0 (get IP from public wireless) -> eth1 (serves IP to the rest of the LAN) -> hub -> LAN

The IP of eth0 is 192.168.1.xxx (gets it from wireless) and I want my LAN to have 192.168.2.xxx.
How do I do that last part?

---

### Post by sparky-steve on 2010-03-09
Hi

Right, the configuration I posted in my previous post is correct, and that should work for you.

Let's concentrate on getting a DHCP server working for you, first.

So, install DHCP server:

```
sudo apt-get install dhcp3-server
```

Edit /etc/dhcp3/dhcpd.conf

I will assume that the IP address on your LAN side is 192.168.2.1 - adjust throughout this config to suit if you're using another IP.

```
option domain-name "HugoMA.local";
#the following line assumes you're also running a DNS server (highly recommended) - if you dont want to, change the address to the DNS server given to you by the ISP
option domain-name-servers 192.168.2.1;
default-lease-time 14400;
ddns-update-style none;
#only bind to the LAN interface eth1
DHCPDARGS=eth1;

subnet 192.168.2.0 netmask 255.255.255.0 {
#the following line assumes you're also running a DNS server (highly recommended) - if you dont want to, change the address to the DNS server given to you by the ISP
        option domain-name-servers 192.168.2.1;
        option domain-name "HugoMA.local";
#the following line is the range of IP addresses to hand out.
 range 192.168.2.200 192.168.2.220;
        option routers 192.168.2.1;
        option subnet-mask 255.255.255.0;
}

#You can set fixed IP addresses for specific hardware like this:
#host HugoMA-Laptop {
#  hardware ethernet 00:AA:11:BB:22:CC;
#  ^ change the hardware address to suit your machines MAC
#  fixed-address 192.168.2.199;
#}


```

Right - that should get you a DHCP server running. Try it, and try to get an IP from the server.

Once that it working, try to connect to the 'net and let's go from there.

SS

---

### Post by HugoMA on 2010-03-10
Hi,

I copied the code to the file and tried to start the server. It failed.
"BlackBox dhcpd: No subnet declaration for eth0 (192.168.1.195)."

I 6then tried this in the interfaces file:
auto eth0
iface eth0 inet dhcp

I have net but still: "BlackBox dhcpd: No subnet declaration for eth0 (192.168.1.195)."

This is my dhcpd.conf:

option domain-name "BlackBox.local";
option domain-name-servers 213.13.145.10; // Local ISP DNS server: ns1.sapo.pt
default-lease-time 14400;
ddns-update-style none;

#only bind to the LAN interface eth1
DHCPDARGS=eth1;

subnet 192.168.2.0 netmask 255.255.255.0 {
#the following line assumes you're also running a DNS server (highly recommended) - if you dont want to, change the address to the DNS server given to you by the ISP
        option domain-name-servers 213.13.145.10;
        option domain-name "BlackBox.local";
#the following line is the range of IP addresses to hand out.
 range 192.168.2.100 192.168.2.120;
        option routers 192.168.2.1;
        option subnet-mask 255.255.255.0;
}

#You can set fixed IP addresses for specific hardware like this:
host BlackBox {
  hardware ethernet 00:30:48:74:ae:0d; // eth1
#  ^ change the hardware address to suit your machines MAC
  fixed-address 192.168.2.10; // the address is still 0.0.0.0 - Checked on network tools
}



I'm not running a dns server.
What are the advantages of having one?

---

### Post by sparky-steve on 2010-03-10
OK. Let's go at this from another angle.

Firstly, open up a terminal and type

```
sudo /etc/init.d/dhcp3-server restart
```Paste the full output of that, please.

Can you also include the full output of interfaces

```
cat /etc/network/interfaces
```and 

```
 ifconfig
```I think you're closer than it looks..... I'm around all afternoon (UK) so will help if I can.

SS

---

### Post by sparky-steve on 2010-03-10
I missed a skip in my original DHCP server configuration.

Check /etc/default/dhcp3-server

For you, it should read something like:
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"
```but only this part is important:

```
INTERFACES="eth1"
```

SS

---

### Post by HugoMA on 2010-03-10
Hugo@BlackBox:~$ sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3
 * check syslog for diagnostics.
                                                                                          [fail]
Hugo@BlackBox:~$ 


/etc/default/dhcp3-server:

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"



/etc/network/interfaces:

auto lo
iface lo inet loopback


ifconfig:

reset@BlackBox:~$ ifconfig
eth0    Link encap:Ethernet  HWaddr 00:30:48:74:ae:0c  
          inet addr:192.168.1.195  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe74:ae0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:452039 (452.0 KB)  TX bytes:53606 (53.6 KB)

eth1    Link encap:Ethernet  HWaddr 00:30:48:74:ae:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by sparky-steve on 2010-03-10
Ah.... now we're getting somewhere :-)

Your eth1 (LAN side, 192.168.2.1) has no IP address assigned.

edit /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.2.1
    netmask 255.255.255.0
```Once you've edited the file, in a terminal:

```
/etc/init.d/networking restart
```then

```
ifconfig
```and check that eth0 has a wireless DHCP address 192.168.1.x and that eth1 now has a fixed LAN address of 192.168.2.1

If so, try restarting the DHCP server again

```
sudo /etc/init.d/dhcp3-server restart
```SS

---

### Post by HugoMA on 2010-03-11
Sorry it took me a while to respond.

One of the computers (the only one I tested) detects the network, gets and address within the defined parameters (192.168.2.xxx), subnet, gateway and dns (213.13.145.10) are also correct, but when I try to go online it stops for a while  on "resolving server" ([www.google.pt](www.google.pt)) and stops on "server not found".

any ideas?

---

### Post by sparky-steve on 2010-03-11
What happens when you surf using IP address?

put [http://216.239.59.105/](http://216.239.59.105/) into your browser.

If it works, we need to work on your DNS; If it doesnt, we need to fault find some more.

This will give us a good indicator on how to proceed.

SS

---

### Post by HugoMA on 2010-03-11
"waiting for 216.239.59.105"

and nothing.

Meanwhile the Ubuntu machine (this one) still has internet.

---

### Post by sparky-steve on 2010-03-11
please post the output of:

```
shorewall status
```

and

```
iptables -L
```

and 

```
ipconfig
```

---

### Post by HugoMA on 2010-03-11
Shorewall:

Hugo@BlackBox:~$ shorewall status
Shorewall-4.2.10 Status at BlackBox - Thu Mar 11 15:25:40 AZOT 2010

Shorewall is stopped
State:Unknown

Hugo@BlackBox:~$ sudo shorewall start
[sudo] password for Hugo: 
   Shorewall is already running
Hugo@BlackBox:~$ 


iptables:

Hugo@BlackBox:~$ iptables -L
iptables v1.4.4: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
Hugo@BlackBox:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
eth0_in    all  --  anywhere             anywhere            
eth1_in    all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
Reject     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:INPUT:REJECT:' 
reject     all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
eth0_fwd   all  --  anywhere             anywhere            
eth1_fwd   all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
Reject     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:FORWARD:REJECT:' 
reject     all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
eth0_out   all  --  anywhere             anywhere            
eth1_out   all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
Reject     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:OUTPUT:REJECT:' 
reject     all  --  anywhere             anywhere            

Chain Drop (1 references)
target     prot opt source               destination         
reject     tcp  --  anywhere             anywhere            tcp dpt:auth 
dropBcast  all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp fragmentation-needed 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
dropInvalid  all  --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            multiport dports loc-srv,microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn 
DROP       udp  --  anywhere             anywhere            udp spt:netbios-ns dpts:1024:65535 
DROP       tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpt:1900 
dropNotSyn  tcp  --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            udp spt:domain 

Chain Reject (4 references)
target     prot opt source               destination         
reject     tcp  --  anywhere             anywhere            tcp dpt:auth 
dropBcast  all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp fragmentation-needed 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
dropInvalid  all  --  anywhere             anywhere            
reject     udp  --  anywhere             anywhere            multiport dports loc-srv,microsoft-ds 
reject     udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn 
reject     udp  --  anywhere             anywhere            udp spt:netbios-ns dpts:1024:65535 
reject     tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpt:1900 
dropNotSyn  tcp  --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            udp spt:domain 

Chain all2all (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
Reject     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:all2all:REJECT:' 
reject     all  --  anywhere             anywhere            

Chain dropBcast (2 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            PKTTYPE = broadcast 
DROP       all  --  anywhere             anywhere            PKTTYPE = multicast 

Chain dropInvalid (2 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            state INVALID 

Chain dropNotSyn (2 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 

Chain dynamic (4 references)
target     prot opt source               destination         

Chain eth0_fwd (1 references)
target     prot opt source               destination         
dynamic    all  --  anywhere             anywhere            state INVALID,NEW 
smurfs     all  --  anywhere             anywhere            state INVALID,NEW 
tcpflags   tcp  --  anywhere             anywhere            
net2all    all  --  anywhere             anywhere            

Chain eth0_in (1 references)
target     prot opt source               destination         
dynamic    all  --  anywhere             anywhere            state INVALID,NEW 
smurfs     all  --  anywhere             anywhere            state INVALID,NEW 
tcpflags   tcp  --  anywhere             anywhere            
net2all    all  --  anywhere             anywhere            

Chain eth0_out (1 references)
target     prot opt source               destination         
fw2net     all  --  anywhere             anywhere            

Chain eth1_fwd (1 references)
target     prot opt source               destination         
dynamic    all  --  anywhere             anywhere            state INVALID,NEW 
tcpflags   tcp  --  anywhere             anywhere            
lan2net    all  --  anywhere             anywhere            

Chain eth1_in (1 references)
target     prot opt source               destination         
dynamic    all  --  anywhere             anywhere            state INVALID,NEW 
tcpflags   tcp  --  anywhere             anywhere            
lan2fw     all  --  anywhere             anywhere            

Chain eth1_out (1 references)
target     prot opt source               destination         
fw2lan     all  --  anywhere             anywhere            

Chain fw2lan (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain fw2net (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain lan2fw (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain lan2lan (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain lan2net (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain logdrop (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:logdrop:DROP:' 
DROP       all  --  anywhere             anywhere            

Chain logflags (5 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:logflags:DROP:' 
DROP       all  --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:logreject:REJECT:' 
reject     all  --  anywhere             anywhere            

Chain net2all (2 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
Drop       all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Shorewall:net2all:DROP:' 
DROP       all  --  anywhere             anywhere            

Chain reject (11 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            PKTTYPE = broadcast 
DROP       all  --  anywhere             anywhere            PKTTYPE = multicast 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
DROP       igmp --  anywhere             anywhere            
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     icmp --  anywhere             anywhere            reject-with icmp-host-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited 

Chain shorewall (0 references)
target     prot opt source               destination         

Chain smurfs (2 references)
target     prot opt source               destination         
LOG        all  --  192.168.2.255        anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       all  --  192.168.2.255        anywhere            
LOG        all  --  255.255.255.255      anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       all  --  255.255.255.255      anywhere            
LOG        all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            

Chain tcpflags (4 references)
target     prot opt source               destination         
logflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG 
logflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
logflags   tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
logflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
logflags   tcp  --  anywhere             anywhere            tcp spt:0 flags:FIN,SYN,RST,ACK/SYN 
Hugo@BlackBox:~$ 


ipconfig:

Hugo@BlackBox:~$ ipconfig
No command 'ipconfig' found, did you mean:
 Command 'tpconfig' from package 'tpconfig' (universe)
 Command 'iwconfig' from package 'wireless-tools' (main)
 Command 'ifconfig' from package 'net-tools' (main)
ipconfig: command not found
Hugo@BlackBox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:74:ae:0c  
          inet addr:192.168.1.195  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe74:ae0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:17562351 (17.5 MB)  TX bytes:2585781 (2.5 MB)

eth1      Link encap:Ethernet  HWaddr 00:30:48:74:ae:0d  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe74:ae0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:59308 (59.3 KB)  TX bytes:3464 (3.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33616 (33.6 KB)  TX bytes:33616 (33.6 KB)

Hugo@BlackBox:~$

---

### Post by sparky-steve on 2010-03-11
it concerns me a little that "shorewall status" says its stopped, and yet when you try to start, it says it's already started. the output from "iptables -L" looks good. But just in case:

Can you paste the output of 

```
sudo shorewall restart
```

and on the "test" machine, try to ping "blackbox" (192.168.2.1) and make sure that works; If that does, try to ping 216.239.59.104 ([www.google.com](www.google.com)) from the "test" machine and see if that works.

if the first ping does work, but the second doesn't, then on the blackbox, open a terminal and type

```
tail -f /var/log/messages
```

and whilst that is running, go to test machine and ping 216.239.59.104 again, and see if there are any block/drop messages.

(CTRL-C will cancel the above tail command.)

---

### Post by HugoMA on 2010-03-11
Hugo@BlackBox:~$ sudo shorewall restart
[sudo] password for Hugo: 
Compiling...
Initializing...
Determining Zones...
   IPv4 Zones: net lan
   Firewall Zone: fw
Validating interfaces file...
Validating hosts file...
Pre-processing Actions...
   Pre-processing /usr/share/shorewall/action.Drop...
   Pre-processing /usr/share/shorewall/action.Reject...
Validating Policy file...
Determining Hosts in Zones...
   net Zone: eth0:0.0.0.0/0
   lan Zone: eth1:0.0.0.0/0
Deleting user chains...
Compiling /etc/shorewall/routestopped ...
Creating Interface Chains...
Compiling Common Rules
Adding Anti-smurf Rules
Compiling TCP Flags checking...
Compiling Kernel Route Filtering...
Compiling Martian Logging...
Compiling /etc/shorewall/rules...
Compiling Actions...
Compiling /usr/share/shorewall/action.Drop for Chain Drop...
Compiling /usr/share/shorewall/action.Reject for Chain Reject...
Compiling /etc/shorewall/policy...
Compiling Traffic Control Rules...
Compiling Rule Activation...
Compiling IP Forwarding...
Shorewall configuration compiled to /var/lib/shorewall/.restart
Restarting Shorewall....
Initializing...
Clearing Traffic Control/QOS
Deleting user chains...
Enabling Loopback and DNS Lookups
Creating Interface Chains...
Setting up SMURF control...
Setting up Black List...
Adding Anti-smurf Jumps...
Setting up TCP Flags checking...
Setting up ARP filtering...
Setting up Route Filtering...
Setting up Martian Logging...
Setting up Accept Source Routing...
Setting up SYN Flood Protection...
Setting up Rules...
Setting up Actions...
Creating action chain Drop
Creating action chain Reject
Creating action chain dropBcast
Creating action chain dropInvalid
Creating action chain dropNotSyn
Applying Policies...
Activating Rules...
done.
Hugo@BlackBox:~$ 



Hugo@BlackBox:~$ tail -f /var/log/messages
Mar 11 15:49:37 BlackBox Hugo: Shorewall restarted
Mar 11 15:52:52 BlackBox dhcpd: DHCPDISCOVER from 00:0b:6a:5d:fe:f8 (Hugo_xp) via eth1
Mar 11 15:52:53 BlackBox dhcpd: DHCPOFFER on 192.168.2.101 to 00:0b:6a:5d:fe:f8 (Hugo_xp) via eth1
Mar 11 15:52:53 BlackBox dhcpd: Wrote 0 deleted host decls to leases file.
Mar 11 15:52:53 BlackBox dhcpd: Wrote 0 new dynamic host decls to leases file.
Mar 11 15:52:53 BlackBox dhcpd: Wrote 2 leases to leases file.
Mar 11 15:52:53 BlackBox dhcpd: DHCPREQUEST for 192.168.2.101 (192.168.2.1) from 00:0b:6a:5d:fe:f8 (Hugo_xp) via eth1
Mar 11 15:52:53 BlackBox dhcpd: DHCPACK on 192.168.2.101 to 00:0b:6a:5d:fe:f8 (Hugo_xp) via eth1
Mar 11 15:53:17 BlackBox dhcpd: DHCPINFORM from 192.168.2.101 via eth1: not authoritative for subnet 192.168.2.0
Mar 11 15:53:20 BlackBox dhcpd: DHCPINFORM from 192.168.2.101 via eth1: not authoritative for subnet 192.168.2.0



pinging blackbox no packet loss.
pinging google.com exceded time 100% loss.

---

### Post by sparky-steve on 2010-03-11
ok... edit/create /etc/shorewall/masq

```
#
# Shorewall version 4 - Masq file
#
# For information about entries in this file, type "man shorewall-masq"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-masq.html
#
###############################################################################
#INTERFACE		SOURCE		ADDRESS		PROTO	PORT(S)	IPSEC	MARK
eth0 eth1
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
```

then

```
sudo shorewall restart
```

and try again......

Meanwhile I'm going to think this through again, and find out which step I've forgotten.... 

keep smiling !!!!

SS

---

### Post by sparky-steve on 2010-03-11
Hugo,

When you installed and first run shorewall, some extra config files should have been created.

please run: 

```
ls -lash /etc/shorewall
```

to check that all necessary files are there.

We cant be that far away from success :-)

SS

---

### Post by HugoMA on 2010-03-11
total 48K
4.0K drwxr-xr-x   2 root root 4.0K 2010-03-11 16:32 .
 12K drwxr-xr-x 131 root root  12K 2010-03-11 14:09 ..
4.0K -rw-r--r--   1 root root  469 2010-03-09 10:13 interfaces
4.0K -rw-r--r--   1 root root  453 2007-11-15 22:24 Makefile
4.0K -rw-r--r--   1 root root  410 2010-03-11 16:32 masq
4.0K -rw-r--r--   1 root root  484 2010-03-09 10:13 policy
4.0K -rw-r--r--   1 root root  580 2010-03-09 10:15 rules
8.0K -rw-r--r--   1 root root 4.1K 2009-06-23 15:23 shorewall.conf
4.0K -rw-r--r--   1 root root  419 2010-03-09 10:14 zones


masq disn't exist.

---

### Post by sparky-steve on 2010-03-11
I assume the masq file didnt make any difference?

There is an important file missing - I cannot fathom why it wasnt created. Anyway, here's mine - i'm hoping it will work for you.

/etc/shorewall/modules

```
#
# Shorewall version 3.0 - Modules File
#
# /etc/shorewall/modules
#
#	This file loads the modules needed by the firewall.
#
#	THE ORDER OF THE COMMANDS BELOW IS IMPORTANT!!!!!! You MUST load in
#	dependency order. i.e., if M2 depends on M1 then you must load M1
#	before you load M2.
#
# For additional information, see
# http://shorewall.net/Documentation.htm#modules
#
###############################################################################
#
# Essential Modules
#
loadmodule ip_tables
loadmodule iptable_filter
loadmodule ip_conntrack
#
# Helpers
#
loadmodule ip_conntrack_pptp
loadmodule ip_nat_pptp
loadmodule ip_conntrack_ftp
loadmodule ip_conntrack_tftp
loadmodule ip_conntrack_irc
loadmodule iptable_nat
loadmodule ip_nat_ftp
loadmodule ip_nat_tftp
loadmodule ip_nat_irc
loadmodule ip_set
loadmodule ip_set_iphash
loadmodule ip_set_ipmap
loadmodule ip_set_macipmap
loadmodule ip_set_portmap
#
# Traffic Shaping
#
loadmodule sch_sfq
loadmodule sch_ingress
loadmodule sch_htb
loadmodule cls_u32
#
# Extensions
#
loadmodule ipt_addrtype
loadmodule ipt_ah
loadmodule ipt_CLASSIFY
loadmodule ipt_CLUSTERIP
loadmodule ipt_comment
loadmodule ipt_connmark
loadmodule ipt_CONNMARK
loadmodule ipt_conntrack
loadmodule ipt_dscp
loadmodule ipt_DSCP
loadmodule ipt_ecn
loadmodule ipt_ECN
loadmodule ipt_esp
loadmodule ipt_hashlimit
loadmodule ipt_helper
loadmodule ipt_iprange
loadmodule ipt_length
loadmodule ipt_limit
loadmodule ipt_LOG
loadmodule ipt_mac
loadmodule ipt_mark
loadmodule ipt_MARK
loadmodule ipt_MASQUERADE
loadmodule ipt_multiport
loadmodule ipt_NETMAP
loadmodule ipt_NOTRACK
loadmodule ipt_owner
loadmodule ipt_physdev
loadmodule ipt_pkttype
loadmodule ipt_policy
loadmodule ipt_realm
loadmodule ipt_recent
loadmodule ipt_REDIRECT
loadmodule ipt_REJECT
loadmodule ipt_SAME
loadmodule ipt_sctp
loadmodule ipt_set
loadmodule ipt_state
loadmodule ipt_tcpmss
loadmodule ipt_TCPMSS
loadmodule ipt_tos
loadmodule ipt_TOS
loadmodule ipt_ttl
loadmodule ipt_TTL
loadmodule ipt_ULOG
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

Get back to me after you've created the above and run

```
shorewall restart
```

I have my fingers crossed......

SS

---

### Post by HugoMA on 2010-03-11
I created the file and restarted both computers. didn't work, maybe cause it's another install. now it get's stuck on aquiring, but gets the ip, dns, etc.

I'll try and set up a standard XP install.

When I connected the cable directly even worse, but that's because the cable is crossover.
The cable works fine (I use it also for my standard DSL modem, so it works and also does the hub/switch.

Pinging internaly works fine on both ways (didn't before from this one to the XP) but from the XP still doesn't ping outside the LAN.

I started this process from a new installation from the CD I downloaded from the Ubuntu site.


Are there any "presets" or software that were supposed to be before starting the bridge?

---

### Post by sparky-steve on 2010-03-11
no..... i've been doing this for many years now, and cannot for the life of me fathom why it isnt working.

All you need is:

-shorewall to share the connection
-DHCP server to give an IP to the LAN side (optional - you can set fixed IPs)
-2 network cards

And the config files I've given you have worked for me for many years. In fact, they are on my current working firewall!!!!

I will think some more tonight, and I'll come back tomorrow.

In the meantime, it might be worth checking all of the config files for shorewall.  Because you cannot ping through blackbox to the internet, the issue is with shorewall at this time.

Sorry, this should be *so* much easier normally....

SS

---

### Post by sparky-steve on 2010-03-11
HugoMA,

Compare what we've done in /etc/shorewall with the example files in /usr/share/doc/shorewall-common/examples/two-interfaces

they should be fundamentally the same. (be careful if you use those examples and change the zone names for example use loc not lan....)

remember - if you make any changes you must restart shorewall

```
sudo shorewall restart
```

SS

---

### Post by HugoMA on 2010-03-15
interfaces:

example
#ZONE    INTERFACE    BROADCAST    OPTIONS
net     eth0            detect          dhcp,tcpflags,nosmurfs,routefilter,logmartians
loc     eth1            detect          tcpflags,nosmurfs,routefilter,logmartians

using
#ZONE    INTERFACE    BROADCAST    OPTIONS
net eth0 detect routefilter,tcpflags,nosmurfs
lan eth1 detect tcpflags


masq:
both equal


policy:
using
fw     net     ACCEPT
lan    net    ACCEPT
lan    lan    ACCEPT
lan    fw    ACCEPT
fw    lan    ACCEPT
net     all    DROP        info
all    all    REJECT        info

example
# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc        net        ACCEPT
loc        $FW        REJECT        info
loc        all        REJECT        info

#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW        net        REJECT        info
$FW        loc        REJECT        info
$FW        all        REJECT        info

#
# Policies for traffic originating from the Internet zone (net)
#
net        $FW        DROP        info
net        loc        DROP        info
net        all        DROP        info

# THE FOLLOWING POLICY MUST BE LAST
all        all        REJECT        info



rules:
example
#############################################################################################################
#ACTION        SOURCE        DEST        PROTO    DEST    SOURCE        ORIGINAL    RATE        USER/    MARK
#                            PORT    PORT(S)        DEST        LIMIT        GROUP
#
#    Accept DNS connections from the firewall to the network
#
DNS/ACCEPT    $FW        net
#
#    Accept SSH connections from the local network for administration
#
SSH/ACCEPT    loc        $FW
#
#    Allow Ping from the local network
#
Ping/ACCEPT    loc        $FW

#
# Drop Ping from the "bad" net zone.. and prevent your log from being flooded..
#

Ping/DROP    net        $FW

ACCEPT        $FW        loc        icmp
ACCEPT        $FW        net        icmp
#


using
SECTION NEW
#




zones:
using
#                    OPTIONS            OPTIONS
fw    firewall
net ipv4
lan ipv4

example
#                    OPTIONS            OPTIONS
fw    firewall
net    ipv4
loc    ipv4


shorewall.conf
Main diferences
using
IP_FORWARDING=Keep
CLAMPMSS=No
ROUTE_FILTER=Yes
OPTIMIZE=0
EXPORTPARAMS=Yes
EXPAND_POLICIES=Yes
KEEP_RT_TABLES=No
DELETE_THEN_ADD=Yes
MULTICAST=No
DONT_LOAD=
AUTO_COMMENT=Yes
MANGLE_ENABLED=Yes
USE_DEFAULT_RT=No
RESTORE_DEFAULT_ROUTE=Yes
FAST_STOP=No

example
IP_FORWARDING=On
CLAMPMSS=Yes
ROUTE_FILTER=No
OPTIMIZE=1
EXPORTPARAMS=No
EXPAND_POLICIES=No
EXPAND_POLICIES=Yes
KEEP_RT_TABLES=No
DELETE_THEN_ADD=Yes
MULTICAST=No
DONT_LOAD=
AUTO_COMMENT=Yes
MANGLE_ENABLED=Yes


extra files:
using:
modules

example:
routestopped

---

### Post by sparky-steve on 2010-03-15
This is a strange one.

> shorewall.conf
Main diferences
using
IP_FORWARDING=Keep
CLAMPMSS=No
ROUTE_FILTER=Yes
OPTIMIZE=0
EXPORTPARAMS=Yes
EXPAND_POLICIES=Yes
KEEP_RT_TABLES=No
DELETE_THEN_ADD=Yes
MULTICAST=No
DONT_LOAD=
AUTO_COMMENT=Yes
MANGLE_ENABLED=Yes
USE_DEFAULT_RT=No
RESTORE_DEFAULT_ROUTE=Yes
FAST_STOP=No

Change this one line in the file:

```
IP_FORWARDING=Yes
```

See if that is the little error....

On your next reply, please let me know what you can & cannot do from both blackbox and the test machine.

ie. ping local, ping web, dns lookups (nslookup [www.google.com](www.google.com)) etc.

I cannot see anything obvious wrong with your config.

---

### Post by sparky-steve on 2010-04-02
Did you resolve this? Id be interested to know! :)

SS

---

### Post by HugoMA on 2010-04-09
Sorry to have taken so long to post.

I have tried connecting my home router to eth0 and the hub to eth1 and still it doesn't work for internet, only intranet.


I think I'm gonna quit this idea and just pay for internet.

Thank you very much for your help.


I'm gonna keep using the forums for other stuff that will surelly come, but for now I say my goodbyes.

Here's my e-mail if you get new ideas.
[email]hugoma5@hotmail.com[/email]

Once again, thank you very much.

---

