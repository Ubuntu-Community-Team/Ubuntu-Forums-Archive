---
title: "IPTV &amp; UBUNTU settings"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by daybat on 2012-08-12
Hello!

I use Ubuntu on my home server. My ISP provides the IP-TV. I can see TV channels only on Windows XP & Mac OS but only if I connect my laptops directly to my ISP (with out the LAN). But I can not see the TV channels on Ubuntu, which is always connected to ISP.

Please help me.
Here is what I have:

**# uname -a**
```
Linux mice 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

**# grep CONFIG_IP_MULTICAST=y /usr/src/linux-headers-3.2.0-29-generic/.config**
```
CONFIG_IP_MULTICAST=y
```

**# ifconfig**
```
br0       Link encap:Ethernet  HWaddr 1c:7e:e5:fb:6a:a3  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9626977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10035476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5958798391 (5.9 GB)  TX bytes:12094860711 (12.0 GB)

eth0      Link encap:Ethernet  HWaddr 54:04:a6:94:fa:3f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9617446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10023485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6092336068 (6.0 GB)  TX bytes:12083582094 (12.0 GB)
          Interrupt:54 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:02:44:37:44:7b  
          inet addr:1.1.1.1  Bcast:1.1.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:606005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552897 errors:0 dropped:0 overruns:5 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:510486302 (510.4 MB)  TX bytes:106214423 (106.2 MB)
          Interrupt:16 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7690054 (7.6 MB)  TX bytes:7690054 (7.6 MB)

mon.wlan1 Link encap:UNSPEC  HWaddr 1C-7E-E5-FB-6A-A3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:297443 (297.4 KB)  TX bytes:0 (0.0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:95.72.5.2  P-t-P:77.51.191.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:601728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:550777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:496979305 (496.9 MB)  TX bytes:93969961 (93.9 MB)

wlan1     Link encap:Ethernet  HWaddr 1c:7e:e5:fb:6a:a3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1316880 (1.3 MB)  TX bytes:12370793 (12.3 MB)
```

**# route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp1
1.1.1.0         0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth1
77.51.191.254   0.0.0.0         255.255.255.255 UH    0      0        0 ppp1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 eth1
```

**# cat /etc/cgi-bin/iptables.rules.sh **
```
#! /bin/sh
#
#######################
# &#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1072; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1086;&#1074;
#######################
 
#iptables -A OUTPUT -j LOG
# Internet (&#1055;&#1086;&#1084;&#1077;&#1085;&#1103;&#1081;&#1090;&#1077; &#1085;&#1072; &#1074;&#1072;&#1096; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;-&#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;)
Inet_zero="eth1"
Inet_Interface="ppp1"
 
# Lan (&#1087;&#1086;&#1084;&#1077;&#1085;&#1103;&#1081;&#1090;&#1077; &#1085;&#1072; &#1074;&#1072;&#1096; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089; &#1089;&#1077;&#1090;&#1077;&#1074;&#1086;&#1075;&#1086; &#1084;&#1086;&#1089;&#1090;&#1072;)
Lan_Interface="br0"
 
# Lo (&#1083;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1080;&#1085;&#1090;&#1077;&#1092;&#1077;&#1081;&#1089; - &#1087;&#1077;&#1090;&#1083;&#1103;)
Lo_Interface="lo"
 
# &#1054;&#1087;&#1080;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; &#1087;&#1091;&#1090;&#1100; &#1076;&#1086; iptables
IPT="/sbin/iptables"
 
# &#1054;&#1095;&#1080;&#1097;&#1072;&#1077;&#1084; &#1090;&#1077;&#1082;&#1091;&#1097;&#1080;&#1077; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072; (&#1077;&#1089;&#1083;&#1080; &#1074;&#1076;&#1088;&#1091;&#1075; &#1077;&#1089;&#1090;&#1100; &#1082;&#1072;&#1082;&#1080;&#1077;-&#1090;&#1086; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072;)
 
$IPT -F
$IPT -t nat -F
$IPT -t mangle -F
 
$IPT -X
$IPT -t nat -X
$IPT -t mangle -X
 
# &#1047;&#1072;&#1076;&#1072;&#1077;&#1084; &#1087;&#1086;&#1083;&#1080;&#1090;&#1080;&#1082;&#1080; &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102;
 
$IPT -P INPUT DROP
$IPT -P FORWARD DROP
$IPT -P OUTPUT DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1085;&#1077;&#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1100;&#1085;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;.
# bad_packets
 
$IPT -N bad_packets
 
$IPT -A bad_packets -p tcp --tcp-flags SYN,ACK SYN,ACK -m state --state NEW -j REJECT --reject-with tcp-reset
$IPT -A bad_packets -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "New not syn:"
$IPT -A bad_packets -p tcp ! --syn -m state --state NEW -j DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1074;&#1093;&#1086;&#1076;&#1103;&#1097;&#1080;&#1093; (&#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;) tcp &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081;.
# tcp_p
$IPT -N tcp_p
 
# &#1063;&#1090;&#1086;&#1073;&#1099;, &#1085;&#1072;&#1087;&#1088;&#1080;&#1084;&#1077;&#1088;, &#1088;&#1072;&#1079;&#1088;&#1077;&#1096;&#1080;&#1090;&#1100; &#1087;&#1086;&#1076;&#1082;&#1083;&#1102;&#1095;&#1072;&#1090;&#1100;&#1089;&#1103; &#1082; &#1085;&#1072;&#1096;&#1077;&#1084;&#1091; &#1096;&#1083;&#1102;&#1079;&#1091; &#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072; &#1087;&#1086; ssh:
##ssh="22"
##ssh_ip_allowed="0/0"
##$IPT -A tcp_p -p tcp -s $ssh_ip_allowed --dport $ssh -j ACCEPT

#i2p
#i2p="8887"
#$IPT -A tcp_p -p tcp -s $Inet_Interface --dport $i2p -j ACCEPT
#$IPT -A udp_p -p udp -s $Inet_Interface --dport $i2p -j ACCEPT
 
$IPT -A tcp_p -p tcp -s 0/0 -j DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1074;&#1093;&#1086;&#1076;&#1103;&#1097;&#1080;&#1093; (&#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;) udp &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081;.
# udp_p
$IPT -N udp_p
 
$IPT -A udp_p -p udp -s 0/0 -j DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1074;&#1093;&#1086;&#1076;&#1103;&#1097;&#1080;&#1093; (&#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;) icmp &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081;.
# icmp_p
$IPT -N icmp_p
 
# &#1056;&#1072;&#1079;&#1088;&#1077;&#1096;&#1072;&#1077;&#1084; "&#1087;&#1080;&#1085;&#1075;&#1086;&#1074;&#1072;&#1090;&#1100;" &#1085;&#1072;&#1096; &#1096;&#1083;&#1102;&#1079; &#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;:
 
$IPT -A icmp_p -p icmp -s 0/0 --icmp-type 8 -j ACCEPT
$IPT -A icmp_p -p icmp -s 0/0 --icmp-type 11 -j ACCEPT
 
$IPT -A icmp_p -p icmp -s 0/0 -j DROP
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; INPUT
 
$IPT -A INPUT -p tcp -j bad_packets
 
$IPT -A INPUT -p all -i $Lan_Interface -j ACCEPT
$IPT -A INPUT -p all -i $Lo_Interface -j ACCEPT
 
$IPT -A INPUT -p all -i $Inet_Interface -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INPUT -p tcp -i $Inet_Interface -j tcp_p
$IPT -A INPUT -p udp -i $Inet_Interface -j udp_p
$IPT -A INPUT -p icmp -i $Inet_Interface -j icmp_p
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; FORWARD
 
$IPT -A FORWARD -p tcp -j bad_packets
 
$IPT -A FORWARD -p all -i $Lan_Interface -j ACCEPT
$IPT -A FORWARD -p all -i $Lo_Interface -j ACCEPT
$IPT -A FORWARD -p all -i $Inet_Interface -m state \
--state ESTABLISHED,RELATED -j ACCEPT
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; OUTPUT
 
$IPT -A OUTPUT -p tcp -j bad_packets
 
$IPT -A OUTPUT -p all -o $Inet_Interface -j ACCEPT
$IPT -A OUTPUT -p all -o $Lan_Interface -j ACCEPT
$IPT -A OUTPUT -p all -o $Lo_Interface -j ACCEPT
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; POSTROUTING (&#1090;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; nat)
 
$IPT -t nat -A POSTROUTING -o $Lan_Interface -j MASQUERADE
$IPT -t nat -A POSTROUTING -o $Inet_Interface -j MASQUERADE
 

# &#1093;&#1077;&#1088;&#1100;
#$IP -I INPUT -p udp --dport 68 -j ACCEPT

#IPTV
/sbin/modprobe ipt_TTL
$IPT -A FORWARD -p igmp -i $Inet_zero -o $Lan_Interface -j ACCEPT
$IPT -I INPUT -i $Inet_zero -s 0.0.0.0/0 -d 224.0.0.0/4 -p udp -j ACCEPT
$IPT -I INPUT -i $Inet_zero -s 0.0.0.0/0 -d 224.0.0.0/4 -p igmp -j ACCEPT
$IPT -A INPUT -d 224.0.0.0/240.0.0.0 -i $Inet_zero -j ACCEPT
$IPT -A INPUT -s 224.0.0.0/240.0.0.0 -i $Inet_zero -j ACCEPT
$IPT -A FORWARD -d 224.0.0.0/240.0.0.0 -j ACCEPT
$IPT -A FORWARD -s 224.0.0.0/240.0.0.0 -j ACCEPT
$IPT -t mangle -A PREROUTING -d 224.0.0.0/240.0.0.0 -j TTL --ttl-inc 1
$IPT -t mangle -A OUTPUT -o $Inet_zero -j TTL --ttl-set 64

#$IPT -A FORWARD -p igmp -i $Inet_Interface -o $Lan_Interface -j ACCEPT
#$IPT -A INPUT -p igmp -j ACCEPT

# PPPoE
$IPT -I FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
 
echo "1" > /proc/sys/net/ipv4/ip_forward
 
echo "Firewall started"
 
exit 0
```

**# cat /etc/igmpproxy.conf **
```
########################################################
#
#   Example configuration file for the IgmpProxy
#   --------------------------------------------
#
#   The configuration file must define one upstream
#   interface, and one or more downstream interfaces.
#
#   If multicast traffic originates outside the
#   upstream subnet, the "altnet" option can be
#   used in order to define legal multicast sources.
#   (Se example...)
#
#   The "quickleave" should be used to avoid saturation
#   of the upstream link. The option should only
#   be used if it's absolutely nessecary to
#   accurately imitate just one Client.
#
########################################################

##------------------------------------------------------
## Enable Quickleave mode (Sends Leave instantly)
##------------------------------------------------------
#quickleave


##------------------------------------------------------
## Configuration for eth2 (Upstream Interface)
##------------------------------------------------------
phyint eth1 upstream  ratelimit 0  threshold 1
	altnet 1.1.1.1/32
	altnet 224.0.0.0/8
	altnet 233.0.0.0/8
	altnet 239.0.0.0/8
	altnet 10.0.0.0/8
	altnet 10.226.96.0/24
#	altnet 192.168.0.0/24

        altnet 77.51.53.0/8 
        altnet 10.0.0.0/8
        altnet 239.255.255.0/24
        altnet 172.16.16.0/24
        altnet 78.107.196.0/22
	altnet 10.226.96.0/24


##------------------------------------------------------
## Configuration for eth0 (Downstream Interface)
##------------------------------------------------------
phyint br0 downstream ratelimit 0 threshold 1
	altnet 192.168.0.0/24
##------------------------------------------------------
## Configuration for lo (Disabled Interface)
##------------------------------------------------------
phyint lo disabled
phyint ppp1 disabled
phyint wlan1 disabled
```

Media play list:
**opentv.m3u**
```
#EXTM3U
#EXTINF:0,&#1055;&#1077;&#1088;&#1074;&#1099;&#1081; &#1082;&#1072;&#1085;&#1072;&#1083;
udp://@233.3.2.1:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; 1
udp://@233.3.2.2:5000
#EXTINF:0,&#1058;&#1042; &#1062;&#1077;&#1085;&#1090;&#1088;
udp://@233.3.2.6:5000
#EXTINF:0,&#1053;&#1058;&#1042;
udp://@233.3.2.4:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; &#1050;
udp://@233.3.2.3:5000
#EXTINF:0,&#1047;&#1074;&#1077;&#1079;&#1076;&#1072;
udp://@233.3.2.12:5000
#EXTINF:0,2&#1093;2
udp://@233.3.2.14:5000
#EXTINF:0,MTV
udp://@233.3.2.15:5000
#EXTINF:0,&#1055;&#1077;&#1090;&#1077;&#1088;&#1073;&#1091;&#1088;&#1075;-5 &#1082;&#1072;&#1085;&#1072;&#1083;
udp://@233.3.2.5:5000
#EXTINF:0,&#1058;&#1042;3
udp://@233.3.2.11:5000
#EXTINF:0,&#1055;&#1077;&#1088;&#1077;&#1094;
udp://@233.3.2.9:5000
#EXTINF:0,&#1057;&#1058;&#1057;
udp://@233.3.2.16:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; 2
udp://@233.3.1.135:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; 24
udp://@233.3.1.137:5000
#EXTINF:0,&#1050;&#1072;&#1088;&#1091;&#1089;&#1077;&#1083;&#1100;
udp://@233.3.1.136:5000
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086;&#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1103; &#1052;&#1072;&#1103;&#1082;
udp://@239.255.4.4:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1042;&#1077;&#1089;&#1090;&#1080; FM
udp://@239.255.4.7:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1069;&#1093;&#1086; &#1052;&#1086;&#1089;&#1082;&#1074;&#1099;
udp://@239.255.4.15:1234
#EXTINF:0,&#1040;&#1074;&#1090;&#1086; &#1088;&#1072;&#1076;&#1080;&#1086;
udp://@239.255.4.12:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1070;&#1084;&#1086;&#1088; FM
udp://@239.255.4.14:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1069;&#1085;&#1077;&#1088;&#1075;&#1080;&#1103;
udp://@239.255.4.11:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1056;&#1086;&#1089;&#1089;&#1080;&#1080;
udp://@239.255.4.6:1234
```

Where is the mistake? What is wrong? Thank's for any help.

---

### Post by bakegoodz on 2012-08-12
There is no information about your IPTV. It's software just may not be compatible. For instance Netflix web access only works on a Windows computer because Silverlight and Silverlight DRM is only on Windows.

---

### Post by larsbj on 2012-09-07
> **daybat said:**
> Hello!

I use Ubuntu on my home server. My ISP provides the IP-TV. I can see TV channels only on Windows XP & Mac OS but only if I connect my laptops directly to my ISP (with out the LAN). But I can not see the TV channels on Ubuntu, which is always connected to ISP.

Please help me.
Here is what I have:

**# uname -a**
```
Linux mice 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```**# grep CONFIG_IP_MULTICAST=y /usr/src/linux-headers-3.2.0-29-generic/.config**
```
CONFIG_IP_MULTICAST=y
```**# ifconfig**
```
br0       Link encap:Ethernet  HWaddr 1c:7e:e5:fb:6a:a3  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9626977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10035476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5958798391 (5.9 GB)  TX bytes:12094860711 (12.0 GB)

eth0      Link encap:Ethernet  HWaddr 54:04:a6:94:fa:3f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9617446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10023485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6092336068 (6.0 GB)  TX bytes:12083582094 (12.0 GB)
          Interrupt:54 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:02:44:37:44:7b  
          inet addr:1.1.1.1  Bcast:1.1.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:606005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552897 errors:0 dropped:0 overruns:5 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:510486302 (510.4 MB)  TX bytes:106214423 (106.2 MB)
          Interrupt:16 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7690054 (7.6 MB)  TX bytes:7690054 (7.6 MB)

mon.wlan1 Link encap:UNSPEC  HWaddr 1C-7E-E5-FB-6A-A3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:297443 (297.4 KB)  TX bytes:0 (0.0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:95.72.5.2  P-t-P:77.51.191.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:601728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:550777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:496979305 (496.9 MB)  TX bytes:93969961 (93.9 MB)

wlan1     Link encap:Ethernet  HWaddr 1c:7e:e5:fb:6a:a3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1316880 (1.3 MB)  TX bytes:12370793 (12.3 MB)
```**# route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp1
1.1.1.0         0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth1
77.51.191.254   0.0.0.0         255.255.255.255 UH    0      0        0 ppp1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 eth1
```**# cat /etc/cgi-bin/iptables.rules.sh **
```
#! /bin/sh
#
#######################
# &#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1072; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1086;&#1074;
#######################
 
#iptables -A OUTPUT -j LOG
# Internet (&#1055;&#1086;&#1084;&#1077;&#1085;&#1103;&#1081;&#1090;&#1077; &#1085;&#1072; &#1074;&#1072;&#1096; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;-&#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;)
Inet_zero="eth1"
Inet_Interface="ppp1"
 
# Lan (&#1087;&#1086;&#1084;&#1077;&#1085;&#1103;&#1081;&#1090;&#1077; &#1085;&#1072; &#1074;&#1072;&#1096; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089; &#1089;&#1077;&#1090;&#1077;&#1074;&#1086;&#1075;&#1086; &#1084;&#1086;&#1089;&#1090;&#1072;)
Lan_Interface="br0"
 
# Lo (&#1083;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1080;&#1085;&#1090;&#1077;&#1092;&#1077;&#1081;&#1089; - &#1087;&#1077;&#1090;&#1083;&#1103;)
Lo_Interface="lo"
 
# &#1054;&#1087;&#1080;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; &#1087;&#1091;&#1090;&#1100; &#1076;&#1086; iptables
IPT="/sbin/iptables"
 
# &#1054;&#1095;&#1080;&#1097;&#1072;&#1077;&#1084; &#1090;&#1077;&#1082;&#1091;&#1097;&#1080;&#1077; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072; (&#1077;&#1089;&#1083;&#1080; &#1074;&#1076;&#1088;&#1091;&#1075; &#1077;&#1089;&#1090;&#1100; &#1082;&#1072;&#1082;&#1080;&#1077;-&#1090;&#1086; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072;)
 
$IPT -F
$IPT -t nat -F
$IPT -t mangle -F
 
$IPT -X
$IPT -t nat -X
$IPT -t mangle -X
 
# &#1047;&#1072;&#1076;&#1072;&#1077;&#1084; &#1087;&#1086;&#1083;&#1080;&#1090;&#1080;&#1082;&#1080; &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102;
 
$IPT -P INPUT DROP
$IPT -P FORWARD DROP
$IPT -P OUTPUT DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1085;&#1077;&#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1100;&#1085;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;.
# bad_packets
 
$IPT -N bad_packets
 
$IPT -A bad_packets -p tcp --tcp-flags SYN,ACK SYN,ACK -m state --state NEW -j REJECT --reject-with tcp-reset
$IPT -A bad_packets -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "New not syn:"
$IPT -A bad_packets -p tcp ! --syn -m state --state NEW -j DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1074;&#1093;&#1086;&#1076;&#1103;&#1097;&#1080;&#1093; (&#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;) tcp &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081;.
# tcp_p
$IPT -N tcp_p
 
# &#1063;&#1090;&#1086;&#1073;&#1099;, &#1085;&#1072;&#1087;&#1088;&#1080;&#1084;&#1077;&#1088;, &#1088;&#1072;&#1079;&#1088;&#1077;&#1096;&#1080;&#1090;&#1100; &#1087;&#1086;&#1076;&#1082;&#1083;&#1102;&#1095;&#1072;&#1090;&#1100;&#1089;&#1103; &#1082; &#1085;&#1072;&#1096;&#1077;&#1084;&#1091; &#1096;&#1083;&#1102;&#1079;&#1091; &#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072; &#1087;&#1086; ssh:
##ssh="22"
##ssh_ip_allowed="0/0"
##$IPT -A tcp_p -p tcp -s $ssh_ip_allowed --dport $ssh -j ACCEPT

#i2p
#i2p="8887"
#$IPT -A tcp_p -p tcp -s $Inet_Interface --dport $i2p -j ACCEPT
#$IPT -A udp_p -p udp -s $Inet_Interface --dport $i2p -j ACCEPT
 
$IPT -A tcp_p -p tcp -s 0/0 -j DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1074;&#1093;&#1086;&#1076;&#1103;&#1097;&#1080;&#1093; (&#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;) udp &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081;.
# udp_p
$IPT -N udp_p
 
$IPT -A udp_p -p udp -s 0/0 -j DROP
 
# &#1057;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1094;&#1077;&#1087;&#1086;&#1095;&#1082;&#1091; &#1076;&#1083;&#1103; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1080; &#1074;&#1093;&#1086;&#1076;&#1103;&#1097;&#1080;&#1093; (&#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;) icmp &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081;.
# icmp_p
$IPT -N icmp_p
 
# &#1056;&#1072;&#1079;&#1088;&#1077;&#1096;&#1072;&#1077;&#1084; "&#1087;&#1080;&#1085;&#1075;&#1086;&#1074;&#1072;&#1090;&#1100;" &#1085;&#1072;&#1096; &#1096;&#1083;&#1102;&#1079; &#1080;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1072;:
 
$IPT -A icmp_p -p icmp -s 0/0 --icmp-type 8 -j ACCEPT
$IPT -A icmp_p -p icmp -s 0/0 --icmp-type 11 -j ACCEPT
 
$IPT -A icmp_p -p icmp -s 0/0 -j DROP
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; INPUT
 
$IPT -A INPUT -p tcp -j bad_packets
 
$IPT -A INPUT -p all -i $Lan_Interface -j ACCEPT
$IPT -A INPUT -p all -i $Lo_Interface -j ACCEPT
 
$IPT -A INPUT -p all -i $Inet_Interface -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INPUT -p tcp -i $Inet_Interface -j tcp_p
$IPT -A INPUT -p udp -i $Inet_Interface -j udp_p
$IPT -A INPUT -p icmp -i $Inet_Interface -j icmp_p
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; FORWARD
 
$IPT -A FORWARD -p tcp -j bad_packets
 
$IPT -A FORWARD -p all -i $Lan_Interface -j ACCEPT
$IPT -A FORWARD -p all -i $Lo_Interface -j ACCEPT
$IPT -A FORWARD -p all -i $Inet_Interface -m state \
--state ESTABLISHED,RELATED -j ACCEPT
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; OUTPUT
 
$IPT -A OUTPUT -p tcp -j bad_packets
 
$IPT -A OUTPUT -p all -o $Inet_Interface -j ACCEPT
$IPT -A OUTPUT -p all -o $Lan_Interface -j ACCEPT
$IPT -A OUTPUT -p all -o $Lo_Interface -j ACCEPT
 
# &#1062;&#1077;&#1087;&#1086;&#1095;&#1082;&#1072; POSTROUTING (&#1090;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; nat)
 
$IPT -t nat -A POSTROUTING -o $Lan_Interface -j MASQUERADE
$IPT -t nat -A POSTROUTING -o $Inet_Interface -j MASQUERADE
 

# &#1093;&#1077;&#1088;&#1100;
#$IP -I INPUT -p udp --dport 68 -j ACCEPT

#IPTV
/sbin/modprobe ipt_TTL
$IPT -A FORWARD -p igmp -i $Inet_zero -o $Lan_Interface -j ACCEPT
$IPT -I INPUT -i $Inet_zero -s 0.0.0.0/0 -d 224.0.0.0/4 -p udp -j ACCEPT
$IPT -I INPUT -i $Inet_zero -s 0.0.0.0/0 -d 224.0.0.0/4 -p igmp -j ACCEPT
$IPT -A INPUT -d 224.0.0.0/240.0.0.0 -i $Inet_zero -j ACCEPT
$IPT -A INPUT -s 224.0.0.0/240.0.0.0 -i $Inet_zero -j ACCEPT
$IPT -A FORWARD -d 224.0.0.0/240.0.0.0 -j ACCEPT
$IPT -A FORWARD -s 224.0.0.0/240.0.0.0 -j ACCEPT
$IPT -t mangle -A PREROUTING -d 224.0.0.0/240.0.0.0 -j TTL --ttl-inc 1
$IPT -t mangle -A OUTPUT -o $Inet_zero -j TTL --ttl-set 64

#$IPT -A FORWARD -p igmp -i $Inet_Interface -o $Lan_Interface -j ACCEPT
#$IPT -A INPUT -p igmp -j ACCEPT

# PPPoE
$IPT -I FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
 
echo "1" > /proc/sys/net/ipv4/ip_forward
 
echo "Firewall started"
 
exit 0
```**# cat /etc/igmpproxy.conf **
```
########################################################
#
#   Example configuration file for the IgmpProxy
#   --------------------------------------------
#
#   The configuration file must define one upstream
#   interface, and one or more downstream interfaces.
#
#   If multicast traffic originates outside the
#   upstream subnet, the "altnet" option can be
#   used in order to define legal multicast sources.
#   (Se example...)
#
#   The "quickleave" should be used to avoid saturation
#   of the upstream link. The option should only
#   be used if it's absolutely nessecary to
#   accurately imitate just one Client.
#
########################################################

##------------------------------------------------------
## Enable Quickleave mode (Sends Leave instantly)
##------------------------------------------------------
#quickleave


##------------------------------------------------------
## Configuration for eth2 (Upstream Interface)
##------------------------------------------------------
phyint eth1 upstream  ratelimit 0  threshold 1
    altnet 1.1.1.1/32
    altnet 224.0.0.0/8
    altnet 233.0.0.0/8
    altnet 239.0.0.0/8
    altnet 10.0.0.0/8
    altnet 10.226.96.0/24
#    altnet 192.168.0.0/24

        altnet 77.51.53.0/8 
        altnet 10.0.0.0/8
        altnet 239.255.255.0/24
        altnet 172.16.16.0/24
        altnet 78.107.196.0/22
    altnet 10.226.96.0/24


##------------------------------------------------------
## Configuration for eth0 (Downstream Interface)
##------------------------------------------------------
phyint br0 downstream ratelimit 0 threshold 1
    altnet 192.168.0.0/24
##------------------------------------------------------
## Configuration for lo (Disabled Interface)
##------------------------------------------------------
phyint lo disabled
phyint ppp1 disabled
phyint wlan1 disabled
```Media play list:
**opentv.m3u**
```
#EXTM3U
#EXTINF:0,&#1055;&#1077;&#1088;&#1074;&#1099;&#1081; &#1082;&#1072;&#1085;&#1072;&#1083;
udp://@233.3.2.1:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; 1
udp://@233.3.2.2:5000
#EXTINF:0,&#1058;&#1042; &#1062;&#1077;&#1085;&#1090;&#1088;
udp://@233.3.2.6:5000
#EXTINF:0,&#1053;&#1058;&#1042;
udp://@233.3.2.4:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; &#1050;
udp://@233.3.2.3:5000
#EXTINF:0,&#1047;&#1074;&#1077;&#1079;&#1076;&#1072;
udp://@233.3.2.12:5000
#EXTINF:0,2&#1093;2
udp://@233.3.2.14:5000
#EXTINF:0,MTV
udp://@233.3.2.15:5000
#EXTINF:0,&#1055;&#1077;&#1090;&#1077;&#1088;&#1073;&#1091;&#1088;&#1075;-5 &#1082;&#1072;&#1085;&#1072;&#1083;
udp://@233.3.2.5:5000
#EXTINF:0,&#1058;&#1042;3
udp://@233.3.2.11:5000
#EXTINF:0,&#1055;&#1077;&#1088;&#1077;&#1094;
udp://@233.3.2.9:5000
#EXTINF:0,&#1057;&#1058;&#1057;
udp://@233.3.2.16:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; 2
udp://@233.3.1.135:5000
#EXTINF:0,&#1056;&#1086;&#1089;&#1089;&#1080;&#1103; 24
udp://@233.3.1.137:5000
#EXTINF:0,&#1050;&#1072;&#1088;&#1091;&#1089;&#1077;&#1083;&#1100;
udp://@233.3.1.136:5000
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086;&#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1103; &#1052;&#1072;&#1103;&#1082;
udp://@239.255.4.4:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1042;&#1077;&#1089;&#1090;&#1080; FM
udp://@239.255.4.7:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1069;&#1093;&#1086; &#1052;&#1086;&#1089;&#1082;&#1074;&#1099;
udp://@239.255.4.15:1234
#EXTINF:0,&#1040;&#1074;&#1090;&#1086; &#1088;&#1072;&#1076;&#1080;&#1086;
udp://@239.255.4.12:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1070;&#1084;&#1086;&#1088; FM
udp://@239.255.4.14:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1069;&#1085;&#1077;&#1088;&#1075;&#1080;&#1103;
udp://@239.255.4.11:1234
#EXTINF:0,&#1056;&#1072;&#1076;&#1080;&#1086; &#1056;&#1086;&#1089;&#1089;&#1080;&#1080;
udp://@239.255.4.6:1234
```Where is the mistake? What is wrong? Thank's for any help.

Try something like this in your /etc/network/interfaces :

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

#        iface eth1 inet dhcp
#        up route add -net 224.0.0.0 netmask 240.0.0.0 dev eth1
#        dns-nameservers 192.168.100.1
#        up route add default gw 192.168.100.1 dev eth0

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        up route add default gw 192.168.100.1 dev br0
        dns-nameservers 192.168.100.1

        up route add -net 239.0.0.0 netmask 255.0.0.0 dev br0

auto eth1

        iface eth1 inet dhcp
        up route add -net 224.0.0.0 netmask 240.0.0.0 dev eth1

        dns-nameservers 192.168.100.1
#       up route add default gw 192.168.100.1 dev eth0

```

---

