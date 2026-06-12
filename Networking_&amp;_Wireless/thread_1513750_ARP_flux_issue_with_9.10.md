---
title: "ARP flux issue with 9.10"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by hydrogen18 on 2010-06-20
Hi,
I have ubuntu 9.10 being used as my home server box. It has 3 NICs. One is 1000Mbps integrated lan the other 2 are 100 Mbps pci cards.

Here is my ifconfig -a 

```
eth0      Link encap:Ethernet  HWaddr 00:26:18:df:6b:e5  
          inet addr:192.168.12.95  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fedf:6be5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1688693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2001734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1055483128 (1.0 GB)  TX bytes:2184157391 (2.1 GB)
          Interrupt:34 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:90:27:90:22:3c  
          inet addr:68.63.34.151  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::290:27ff:fe90:223c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:195767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61407403 (61.4 MB)  TX bytes:4587931 (4.5 MB)

eth2      Link encap:Ethernet  HWaddr 00:90:27:50:72:a3  
          inet addr:192.168.12.2  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fe50:72a3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6483257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9004980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2597024677 (2.5 GB)  TX bytes:9311126276 (9.3 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:845205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:845205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67943028 (67.9 MB)  TX bytes:67943028 (67.9 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.13.1  P-t-P:192.168.13.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:284 (284.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 1a:45:4c:c0:ab:94  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:102095 (102.0 KB)

```

as you can see, eth0 and eth2 share the same subnet. Eth0 is plugged into my cable modem. I am using iptables to do NAT so all computers can use the internet. ```
#---------------------------------------------------------------
# Load the NAT module
#
# Note: It is best to use the /etc/rc.local example in this
#       chapter. This value will not be retained in the
#       /etc/sysconfig/iptables file. Included only as a reminder.
#---------------------------------------------------------------
 
modprobe iptable_nat

#---------------------------------------------------------------
# Enable routing by modifying the ip_forward /proc filesystem file
#
# Note: It is best to use the /etc/sysctl.conf example in this
#       chapter. This value will not be retained in the
#       /etc/sysconfig/iptables file. Included only as a reminder.
#---------------------------------------------------------------
 
echo 1 > /proc/sys/net/ipv4/ip_forward

 
#---------------------------------------------------------------
# Disable routing triangulation. Respond to queries out
# the same interface, not another. Helps to maintain state
# Also protects against IP spoofing
#---------------------------------------------------------------
 
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter 
 
 
#---------------------------------------------------------------
# Enable logging of packets with malformed IP addresses
#---------------------------------------------------------------
 
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians 
 
 
#---------------------------------------------------------------
# Disable redirects
#---------------------------------------------------------------
 
echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects
 
 
#---------------------------------------------------------------
# Disable source routed packets
#---------------------------------------------------------------
 
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route 
 
 
#---------------------------------------------------------------
# Disable acceptance of ICMP redirects
#---------------------------------------------------------------
 
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
 
 
#---------------------------------------------------------------
# Turn on protection from Denial of Service (DOS) attacks
#---------------------------------------------------------------
 
echo 1 > /proc/sys/net/ipv4/tcp_syncookies 
 
 
#---------------------------------------------------------------
# Disable responding to ping broadcasts
#---------------------------------------------------------------
 
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
 
 
#---------------------------------------------------------------
# Allow masquerading
# - Interface eth0 is the internet interface
# - Interface eth1 is the private network interface
#---------------------------------------------------------------
 
iptables -A POSTROUTING -t nat -o $EXTIFACE -s $PRIVATE_NET -d 0/0 \
         -j MASQUERADE

#create 3 chains
#whitelist, greylist, and blacklist

iptables -N whitelist
iptables -N greylist
iptables -N blacklist
#iptables -A whitelist -j LOG
#iptables -A greylist -j LOG



#based on source ip, filter packets into each chain
iptables -A FORWARD -s $GREYLIST -i $INTIFACE -j greylist
iptables -A FORWARD -s $WHITELIST -i $INTIFACE -j whitelist
#iptables -A FORWARD -j LOG

#------
#allow all whitelisted traffic through


#allow new connections from  interal to external
iptables -A whitelist  -o $EXTIFACE -m state  \
        --state NEW,ESTABLISHED,RELATED -j ACCEPT
#accept existing connection packets from external to internal
iptables -A whitelist -i $EXTIFACE  -m state \
        --state ESTABLISHED,RELATED -j ACCEPT

#allow icmp
 


#---
#allow limited greylist traffic

#allowed a limited set of commonly used port
iptables -A greylist -p tcp -m multiport --dports 80,22,443,37,110,25,5050,5190,1080,8080,5222,5223,1863 -o $EXTIFACE -m state\
        --state NEW,ESTABLISHED,RELATED -j ACCEPT

#allow udp 53 both ways for DNS
iptables -A greylist -p udp -m multiport --ports 53 -o $EXTIFACE -m state\
        --state NEW,ESTABLISHED,RELATED -j ACCEPT


#allow traffic from existing connection from external to internal
iptables -A greylist -i $EXTIFACE -m state \
         --state ESTABLISHED,RELATED -j ACCEPT

#reject everything else
iptables -A greylist  -j REJECT --reject-with icmp-net-prohibited 


#---

#port forward some ports from the external interface to destinations on the internal network
#should work only for hosts in whitelist range
iptables -t nat -A PREROUTING -p tcp -i $EXTIFACE -m multiport \
        --dports 22  -m multiport --sports 1024:65535 -j DNAT --to 192.168.12.95
iptables -t nat -A PREROUTING -p tcp -i $EXTIFACE  -m multiport --dports 6000:7000 \
        -m multiport --sports 1024:65535 -j DNAT --to 192.168.12.95
iptables -A FORWARD -p tcp  -i $EXTIFACE -d 192.168.12.95 -m multiport \
        --sports  1024:65535 -m state --state NEW -j ACCEPT

#---
#allow any incoming traffic related to an existing conncetion
iptables -A FORWARD -i $EXTIFACE -m state --state ESTABLISHED,RELATED -j ACCEPT
#reject forwarding everything else on the external interface
iptables -A FORWARD -i $EXTIFACE -j DROP


#---
#drop pings  coming from the external interface
iptables -A INPUT -p icmp --icmp-type echo-request -i $EXTIFACE -j DROP

#defend against syn flood attacks
iptables -A INPUT -p tcp --syn -m limit --limit 5/s -i $EXTIFACE -j ACCEPT

```

I also run dhcp3 server to do DHCP to my local computers. Atm everything is 'working'.

My ideal setup is to use eth2 on 192.168.12.2 as my default gateway. All traffic bound for the internet should physically pass across this interface. Eth0 should be on 192.168.12.95. The reason for this is if  I am backing up my laptop to my firewall(it has RAID10 array in it) I do not want to saturate the same connection my room mates must use for internet (should be eth2). 

I have no problems with eth1, it is connected to my cable modem. Eth0 is plugged into a gigabit switch. Eth2 is plugged into a dd wrt. The dd wrt device is plugged into the gigabit switch as well. My problem is that eth0 answers all arp requests for eth2. This mean all traffic is traversing eth0. Logically I tried setting 

```

sysctl -w net.ipv4.conf.all.arp_ignore=1
sysctl -w net.ipv4.conf.all.arp_announce=2
```

After which I can still reach 192.168.12.95. I cannot reach 192.168.12.2. ARP will not resolve for it. However, clients can still receive an IP from it if I bind dhcp3 server to that interface only. So i think at the hardware/physical layer it must be a good NIC/connection. Obviously, this means no one can get to the internet. 

Interestingly enough, physically unplugging the cable to eth0 I still cannot reach the machine at 192.168.12.2 via eth2. Even after clearing client arp caches it will not resolve. 

This is really torque'ing my brain. I have no idea what is going on. Any advice will be helpful

---

