---
title: "2 NIC transparent squid"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by Illsuions on 2011-04-06
Hi, wanted to say what a great site an community this has been for me.
Hopefully it won't matter but just an FYI I am Linux novice, though I have been able to pick up some basics fairly quick with the wealth of information on this site and others. That being said...

I managed to build a transparent squid proxy on machine that I set up, in hopes to implement it for one of my clients. I have everything set up and running through one NIC. I want to direct some traffic through the second NIC. My set up looks like this

WAN
    [COLOR=Red]|[/COLOR]
DD-WRT[COLOR=Red] ---->[/COLOR]Switch [COLOR=Red]---->[/COLOR]client CP's
     [COLOR=Red]|[/COLOR]
Squid server (2NIC)


Currently DD-WRT redirects all traffic to squid [COLOR=Red]eth1-192.168.0.100:3128[/COLOR] which obviously sends it back out to the client CP's. I would like to be able to redirect all traffic going back out to client CP's through my second NIC [COLOR=Red]eth2-192.168.0.101 [/COLOR]

If anyone needs any other information I will be happy to provide. Thanks!

---

### Post by SeijiSensei on 2011-04-06
Quick overview:

Disconnect the switch from the DD-WRT router and plug that cable into the second NIC.  Assign that card a static address in the same IP space as the client machines. Basically you'll be making the Linux box the main router and just forwarding traffic out to the Internet via the DD-WRT router.  In fact, if you configure firewalling and DHCP services on the Linux box correctly, you can dispense with the DD-WRT router entirely and connect eth0 directly to the WAN.

If you continue to rely on the DD-WRT router for DHCP assignments, you'll need to run [dhcp-helper]("http://manpages.ubuntu.com/manpages/lucid/man8/dhcp-helper.8.html") on this box so the workstations' requests are passed to the DD-WRT router.  If you're industrious, you could install dhcp3-server on the box and have it do the assignments instead.  Make sure the DHCP server (wherever it's located) gives the workstations the second NIC's address as their default gateway.  Right now the router's LAN address is the default gateway.

Make sure IP forwarding is enabled in the kernel (see /etc/sysctl.conf for details).  You'll need to include a iptables NAT rule to forward any other traffic besides HTTP out to the Internet.

(You seem to have eth1 and eth2 as the interface addresses.  Normally they're designated eth0 and eth1.  Numbering in the *nix world usually starts with zero.  Do you actually have another Ethernet port, say a built-in one on the motherboard, that is assigned eth0?  What does "ifconfig -a" say?)

---

### Post by Illsuions on 2011-04-06
Thanks for the quick responce!

For whatever reason my interface addresses are listed as eth1 and eth2, no other Ethernet port.

eth1      Link encap:Ethernet  HWaddr 00:0f:fe:67:df:85  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe67:df85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9217015 (9.2 MB)  TX bytes:470613 (470.6 KB)
          Interrupt:19 Memory:f0500000-f0520000 

eth2      Link encap:Ethernet  HWaddr 5c:d9:98:09:f6:ad  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5ed9:98ff:fe09:f6ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7101 (7.1 KB)  TX bytes:7504 (7.5 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

I realise this is not a dd-wrt forum but for the sake of maybe someone else's similar situation these are my firewall rules on my router are:
#!/bin/sh
PROXY_IP=192.168.0.100
PROXY_PORT=3128
LAN_IP=`nvram get lan_ipaddr`
LAN_NET=$LAN_IP/`nvram get lan_netmask`

iptables -t nat -A PREROUTING -i br0 -s $LAN_NET -d $LAN_NET -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -i br0 -s ! $PROXY_IP -p tcp --dport 80 -j DNAT --to $PROXY_IP:$PROXY_PORT
iptables -t nat -I POSTROUTING -o br0 -s $LAN_NET -d $PROXY_IP -p tcp -j SNAT --to $LAN_IP
iptables -I FORWARD -i br0 -o br0 -s $LAN_NET -d $PROXY_IP -p tcp --dport $PROXY_PORT -j ACCEPT


[FONT=Verdana]I already delved into a solution for my issue, bonding my two etho connections with ifenslave on mode=0, learning as I go... Maybe you can tell me if it is a reasonable thing to do. Or is what you suggested the more intelligent approach[/FONT].

---

