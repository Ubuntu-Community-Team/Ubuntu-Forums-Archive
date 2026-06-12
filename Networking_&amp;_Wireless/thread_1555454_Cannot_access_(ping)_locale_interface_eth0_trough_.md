---
title: "Cannot access (ping) locale interface eth0 trough VPN"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by okieffer on 2010-08-18
Hello,

I've set up a VPN network to access my office lan from home.

The VPN server is PopTop running on a 10.04 machine. This machine is also acting as a firewall between internet (eth1) and lan (eth0). 
Everything is working OK (I can connect to the resources located on my office lan from home), but the only one I can't access from home is the **locale eth0 of the linux machine**. I guess that this has something to do with the routes and/or the firewall rules but I#ve tried a lot of configurations without success so far.

The network configuration is:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:cd:e3:cb  
          inet addr:192.168.0.250  Bcast:192.168.127.255  Mask:255.255.128.0
          inet6 addr: fe80::221:85ff:fecd:e3cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2068292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3211260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:341078011 (341.0 MB)  TX bytes:4100829447 (4.1 GB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:15:17:0e:65:54  
          inet addr:*<public-ip>*  Bcast:<public>.127  Mask:255.255.255.192
          inet6 addr: *<public-ip>*/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:958645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:723393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:930935608 (930.9 MB)  TX bytes:250931297 (250.9 MB)
          Memory:f0200000-f0220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9657859 (9.6 MB)  TX bytes:9657859 (9.6 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.19.1.6  P-t-P:172.19.1.31  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:45114 (45.1 KB)  TX bytes:816 (816.0 B)



The routes are:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.19.1.31     *               255.255.255.255 UH    0      0        0 ppp0
*<public-ip>*     *               255.255.255.192 U     0      0        0 eth1
192.168.0.0     *               255.255.128.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         213.83.46.65    0.0.0.0         UG    100    0        0 eth1

I also add these rules for the firewall:

$IPT -A FORWARD -i ppp0 -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A POSTROUTING -o ppp0 -j MASQUERADE


the configuration of the windows client on the other side of the VPN is (sorry it is in French) :

carte Ethernet Connexion au réseau local:

        Suffixe DNS propre à la connexion : Speedport_W_700V
        Description . . . . . . . . . . . : Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
        Adresse physique . . . . . . . . .: 00-24-8C-36-2E-1D
        DHCP activé. . . . . . . . . . . : Oui
        Configuration automatique activée . . . . : Oui
        Adresse IP. . . . . . . . .*. . . : 192.168.2.104
        Masque de sous-réseau . . .*. . . : 255.255.255.0
        Passerelle par défaut . . .*. . . : 192.168.2.1
        Serveur DHCP. . . . . . . . . . . : 192.168.2.1
        Serveurs DNS . . . . . . . . . .  : 208.67.222.222
	                                    208.67.220.220
        Bail obtenu . . . . . . . .*. . . : mercredi, août 18, 2010 07:28:55
        Bail expirant . . . . . . .*. . . : mardi, janvier 19, 2038 05:14:07

Carte PPP rational :
        Suffixe DNS propre à la connexion : 
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Adresse physique . . . . . . . . .: 00-53-45-00-00-00
        DHCP activé. . . . . . . . . . . : Non
        Adresse IP. . . . . . . . .*. . . : 172.19.1.31
        Masque de sous-réseau . . .*. . . : 255.255.255.255
        Passerelle par défaut . . .*. . . : 172.19.1.31
        Serveurs DNS . . . . . . . . . .  : 192.168.0.240
	                                    208.67.222.222





Can someone please help me?

Thank you.

---

