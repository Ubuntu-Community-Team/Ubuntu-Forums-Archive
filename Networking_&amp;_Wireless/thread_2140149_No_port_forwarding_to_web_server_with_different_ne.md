---
title: "No port forwarding to web server with different netmask than default netmask."
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by xourbad on 2013-04-28
Hello, 
I have the following config.


Internet  ----(WAN)- pfsense -(DMZ)------(eth0)- COOVA Hostpot box -(eth1)----WIFI + AP Zone

I configured pfsense to forward 8001 to 172.1.1.1 port 8001

And here are COOVA Hotspot BOX (which is an ubuntu 10.04 server release) interfaces: 
eth0: [172.1.1.1/248]("http://172.1.1.1/248")
eth1: [10.0.0.1/16]("http://10.0.0.1/16")


My goal is to port forward port 8001 to several WEB servers APS.

All my APs have a "/24" netmask, ie [10.127.127.11/24]("http://10.127.127.11/24")

On the COOVA, I defined alias eth1:AP1 to [10.127.127.251/24]("http://10.127.127.251/24") in order to ping the AP1 (no ping without this alias)

The web server of the AP1 is ok since "lynx 10.127.127.11" is ok from the COOVA.

But I cannot reach AP1 from internet.

tcpdump shows www queries reaching eth1, but there is no www answer from the AP1.
# tcpdump -i eth1 'host 10.127.127.11'
04:23:40.647819 **ARP, Request who-has 10.127.127.11 tell 10.127.0.1,** length 28
04:23:40.648375 ARP, Reply 10.127.127.11 is-at c0:c1:c0:1a:7a:e1 (oui Unknown), length 46
04:23:40.648387 IP myhomeip.org.53874 > 10.127.127.11.www: Flags [S], seq 3716296767, win 8192, options [mss 1352,nop,wscale 2,sackOK,TS val 14138801 ecr 0], length 0
...
04:23:49.647643 IP myhomeip.org.53874 > 10.127.127.11.www: Flags [S], seq 3716296767, win 8192, options [mss 1352,sackOK,TS val 14139701 ecr0], length 0
04:23:49.897440 IP myhomeip.org.42759 > 10.127.127.11.www: Flags [S], seq 1470074896, win 8192, options [mss 1352,sackOK,TS val 14139726 ecr0], length 0
04:24:13.331817 ARP, Request who-has 10.127.127.11 tell 10.127.0.1, length 2804:24:13.332183 ARP, Reply 10.127.127.11 is-at c0:c1:c0:1a:7a:e1 (oui Unknown), length 46
04:24:17.329358 IP myhomeip.org.51567 > 10.127.127.11.www: Flags [S], seq 2987723356, win 8192, options [mss 1352,sackOK,TS val 14142469 ecr0], length 0
...


I guess the problem in this port forwarding comes from the AP1 netmask set to "24" while default netmask is "16", and netfilter uses 10.127.0.1/16 eth1 interface to send packets
coming from internet, not use virtual interface eth1:AP1 to reach. Perhaps the arp requests reported by tcpdump are related to requests used by the internet request. 


I am at the end of my tests.
I tried some to raise 10.127.127.251 metric route, no success.
I tried some SNAT settings, REDIRECT is from what I understood not relevant for this case. 
As I am not expert in networking nor iptables, I probably missed something. 

Is there an iptables Guru or/and someone who knows more than me about networking stuff?

Thank you, 

Xavier Droubay

Here are below netfiler rules :

# iptables -L -n -v -t filter
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 801K   44M TCPMSS     tcp  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")             [0.0.0.0/0]("http://0.0.0.0/0")           tcp flags:0x06/0x02 TCPMSS clamp to PMTU
  21M 4405M ACCEPT     all  --  eth1   *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")
  31M   37G ACCEPT     all  --  *      eth1    [0.0.0.0/0]("http://0.0.0.0/0")            [ 0.0.0.0/0]("http://0.0.0.0/0")
    0     0 ACCEPT     tcp  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")              [10.127.127.0/24]("http://10.127.127.0/24")     tcp dpt:8011


# iptables -L -n -v -t nat
Chain PREROUTING (policy ACCEPT 758K packets, 59M bytes)
 pkts bytes target     prot opt in     out     source               destination
  103  6180 DNAT       tcp  --  eth0   *       [0.0.0.0/0]("http://0.0.0.0/0")
[0.0.0.0/0]("http://0.0.0.0/0")           tcp dpt:8011 to:[10.127.127.11:80]("http://10.127.127.11:80")

Chain POSTROUTING (policy ACCEPT 7872 packets, 330K bytes)
 pkts bytes target     prot opt in     out     source               destination
 238K   18M MASQUERADE  all  --  *      eth0    [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")

---

### Post by xourbad on 2013-04-28
I forgot to tell you that my goal is to managed the access points from internet. 
Sorry.

---

### Post by Doug S on 2013-04-30
Hi, and welcome to Ubuntu forums.

Sorry, but I find your description a little difficult to follow, and it seems to contain confusion between netmasks and actual IP addresses. Perhaps you could post the output for "ifconfig" for the COOVA box, as I want to know the actual IP addresses of eth0 and eth1, not just their netmasks. And maybe use tcpdump in non-lookup mode, so that we get IP adresses instead of names.

Anyway, isn't your problem somehow at the AP1 end and not the COOVA box? The SYN packets are being sent, but nothing returns. So maybe AP1 doesn't know how to route the return packets.

Also what should this really be?:```
eth0: [[COLOR=#dd4814]172.1.1.1/248[/COLOR]]("http://172.1.1.1/248")
```Things seems unclear (at least to me) between 10.0.0.0/16 and 10.127.127.0/24

---

### Post by xourbad on 2013-05-01
Hi and thanks for your interest.

Sorry for my error : 
eth1: [10.127.0.1/16]("http://10.0.0.1/16")

I had in mind that we are in network 10.0.0.0/16

So from coova

```
# ifconfig #resumed
eth0      Link encap:Ethernet  HWaddr 00:0c:29:f3:32:73
          inet adr:172.1.1.1  Bcast:172.1.1.7  Masque:255.255.255.248
          adr inet6: fe80::20c:29ff:fef3:3273/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
eth1      Link encap:Ethernet  HWaddr 00:0c:29:f3:32:7d
          inet adr:10.127.0.1  Bcast:10.127.255.255  Masque:255.255.0.0
          adr inet6: fe80::20c:29ff:fef3:327d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
eth1:0WRT Link encap:Ethernet  HWaddr 00:0c:29:f3:32:7d
          inet adr:10.127.127.251  Bcast:10.127.127.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:16 Adresse de base:0x20a4
# LC_ALL=C route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.1.1.0       0.0.0.0         255.255.255.248 U     0      0        0 eth0
10.127.1.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.127.127.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.127.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         172.1.1.6       0.0.0.0         UG    100    0        0 eth0

```

Furthermore PFSENSE DMZ has ip address : 172.1.1.6/248

---

### Post by xourbad on 2013-05-02
up

Please I am at the deadlock

Thanks, 
Xavier

---

### Post by Doug S on 2013-05-02
Thanks for your additional information. I don't have anything new to say, and still think:
> **Doug S said:**
> Anyway, isn't your problem somehow at the AP1 end and not the COOVA box? The SYN packets are being sent, but nothing returns. So maybe AP1 doesn't know how to route the return packets.Also, I don't know what you mean by:> The web server of the AP1 is ok since "lynx 10.127.127.11" is ok from the COOVA.but, I still defer to your tcpdump listing that shows no packets being returned. I would look in more detail at AP1.

---

