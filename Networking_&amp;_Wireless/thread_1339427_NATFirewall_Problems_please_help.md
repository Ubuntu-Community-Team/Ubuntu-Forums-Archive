---
title: "NAT/Firewall Problems please help"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by joshajames on 2009-11-27
Hi,

I have been using linux for some time (having completely ditched Windoze about 18Months ago).  This is sadly the first time i've ever asked for help.  I have found these forums to be most useful, so I hope you will help me.

I am trying to get my NAT system working.  I have had this working on other sites but this time i'm completely stumped.  The system is as follows.

Firewall 172.16.0.3 - eth0
Firewall dhcp (usually 10.228.177.*) -wlan0

Laptop 172.16.0.2.  Gateway 172.16.0.3.  The laptop can ping it's self and the firewall.
The firewall has Nat on and all the normal IP tables plus some firewall rules.  Using Wireshark I can see the Firewall sending packets routed from the Laptop to the wlan0 interface, however nothing comes back.  I imagine the IP header re-write is going wrong somewhere.

I've attached my firewall/nat script and iptables -L -v for info

Thanks in advance for any help.

Servers iptables -L -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            state INVALID LOG level warning tcp-options ip-options prefix `DROP INVALID ' 
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    2   104 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 LOG        all  --  eth0   any    !172.16.0.0/24        anywhere            LOG level warning prefix `SPOOFED PKT ' 
    0     0 DROP       all  --  eth0   any    !172.16.0.0/24        anywhere            
    0     0 ACCEPT     tcp  --  eth0   any     172.16.0.0/24        anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  eth0   any     172.16.0.0/24        anywhere            tcp dpt:domain flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp echo-request 
    0     0 LOG        all  --  !lo    any     anywhere             anywhere            LOG level warning tcp-options ip-options prefix `DROP ' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            state INVALID LOG level warning tcp-options ip-options prefix `DROP INVALID ' 
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 LOG        all  --  eth0   any    !172.16.0.0/24        anywhere            LOG level warning prefix `SPOOFED PKT ' 
    0     0 DROP       all  --  eth0   any    !172.16.0.0/24        anywhere            
    0     0 ACCEPT     tcp  --  eth0   any     172.16.0.0/24        anywhere            tcp dpt:ftp flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  eth0   any     172.16.0.0/24        anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  eth0   any     172.16.0.0/24        anywhere            tcp dpt:smtp flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  eth0   any     172.16.0.0/24        anywhere            tcp dpt:whois flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https state NEW 
    0     0 ACCEPT     tcp  --  eth0   any     172.16.0.0/24        anywhere            tcp dpt:4321 flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:domain state NEW 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:bootps state NEW 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:bootps state NEW 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp echo-request 
    0     0 LOG        all  --  !lo    any     anywhere             anywhere            LOG level warning tcp-options ip-options prefix `DROP ' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            state INVALID LOG level warning tcp-options ip-options prefix `DROP INVALID ' 
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    2   104 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  any    any     anywhere             [www.btopenzone.com]("http://www.btopenzone.com")  tcp dpt:8443 flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:smtp flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:whois flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:4321 flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:mdns flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:mdns state NEW 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:bootps state NEW 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:domain flags:FIN,SYN,RST,ACK/SYN state NEW 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain state NEW 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp echo-request 
    0     0 LOG        all  --  any    !lo     anywhere             anywhere            LOG level warning tcp-options ip-options prefix `DROP '

---

### Post by joshajames on 2009-11-27
I know the above is a little messy but i'm on a public (unencrypted) Wireless network here so any security pointers from the above would also be very well accepted.

Servers route is:

172.16.0.0      *               255.255.255.0   U     0      0        0 eth0
10.228.176.0    *               255.255.252.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.228.176.1    0.0.0.0         UG    0      0        0 wlan0

Please help i've been smashing my head off this desk all day and it's starting to hurt.  I need to get this working so I can start working on a VPN to my home address.

Cheers.

Josh

---

### Post by Yoann Juet on 2009-11-27
> **joshajames said:**
> I know the above is a little messy but i'm on a public (unencrypted) Wireless network

I see, that's why your default gw is on your wlan interface...! Well, try this little test:

on your laptop:
# ping 10.228.176.1

on your firewall:
# tshark -i wlan

is IP masquerading working ? You should see outgoing packets with source ip 10.228.(176|177).x.

---

### Post by joshajames on 2009-11-27
The plot thickens!.  If I ping from my laptop the gateway my server has (as per route shown here) I get nothing.  If I ping my servers public ip (10.228.177.xx) I get a reply.  What's going on?  I cannot ping or resolve any other addresses on the laptop.  The servers connection to the internet works perfectly.

172.16.0.0      *               255.255.255.0   U     0      0        0 eth0
10.228.176.0    *               255.255.252.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         **10.228.176.1**    0.0.0.0         UG    0      0        0 wlan0

---

### Post by joshajames on 2009-11-27
The tshark looked as it should (for the address I get no ping response to) so the packets are leaving the server via wlan0.  It shows no packets returning to wlan0 tho

traceroute to a good server gets only as far as my firewall system.

traceroute to 216.239.59.147
1.  doedo.local (172.16.0.3)

***
I'm stumped and very annoyed at it now!](*,)

---

### Post by Yoann Juet on 2009-11-28
> **joshajames said:**
> The plot thickens!.  If I ping from my laptop the gateway my server has (as per route shown here) I get nothing.

Your wlan provider blocks icmp echo packets.

> If I ping my servers public ip (10.228.177.xx) I get a reply.  What's going on?

You can ping every machine on the wlan, except those who are blocking icmp packets.

>   I cannot ping or resolve any other addresses on the laptop.  The servers connection to the internet works perfectly.

DNS issue ?  Your server gets valid DNS server(s) from your wlan provider (/etc/resolv.conf) through DHCP protocol. Ensure that your laptop has the same DNS entries as your server.

---

### Post by joshajames on 2009-11-28
I could see that if the server could not ping remote addresses that accept ICMP but it can.  Also the packets you see when the laptop tries to DNS resolve addresses are headed to the correct IP for my DNS servers.

I've pulled most of my hair out now.

---

### Post by joshajames on 2009-11-29
BUMP.


Anyone help me out on this.  Karma would be yours!.

---

### Post by joshajames on 2009-12-02
Any ideas anyone?  Plz...

---

### Post by teward on 2009-12-02
I hope to god you have a firewall enabled... because otherwise, you're completely exposed to the universe of the interwebz...

---

### Post by joshajames on 2009-12-04
I'm hoping those IPTABLES should keep me secure!.  Still can't figure this NAT/MASQ problem out tho.  Think I may need to give up soon.....:(:(:(

---

### Post by Iowan on 2009-12-04
Though not specifically NAT/Firewall, [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page may provide some useful information.

---

