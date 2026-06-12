---
title: "Two NICs problem"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by FalconDude on 2012-11-05
Hi Guys 

New guy here, I have some exp. with Linux and Ubuntu but not able to solve this problem I have been having, hope it is trivial for you guys. 

I have a system with two NICs. One is onboard. eth0 is the PCI one and eth2 is the onboard one. Now I want to do the whole share internet between the two cards etc etc. 

eth0 is connected to the main network with internet access static IP, eth2 is connected to a router feeding the smaller network with static IP. 

The problem is, the moment the router is turned on, access to the main network is lost from eth0. It doesn't matter if I configure the iptables or ufw anyway, them moment the router goes live, the network access is lost. 

any help greatly appreciated.

---

### Post by albandy on 2012-11-05
Did the main network have a default gateway? Maybe you're dealing with two default gateways.

Turn on the router, wait until your connection is lost, then do: 
route -n 
and post the answer.

---

### Post by FalconDude on 2012-11-05
Thanks man

this is what i have :: 

my ip routing table
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         148.197.34.254  0.0.0.0         UG    0      0        0 eth0
148.197.34.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.5.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2

```
my NICs 

```
 
eth0      Link encap:Ethernet  HWaddr 00:50:da:df:51:62  
          inet addr:148.197.34.51  Bcast:148.197.34.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fedf:5162/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7337 errors:0 dropped:14 overruns:1 frame:0
          TX packets:1444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2333968 (2.3 MB)  TX bytes:246473 (246.4 KB)
          Interrupt:16 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr 00:1c:25:35:bf:f2  
          inet addr:192.168.5.2  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe35:bff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:480 (480.0 B)  TX bytes:8817 (8.8 KB)
          Interrupt:23 Base address:0x4000 
```My iptables BEFORE the router goes live !

```


sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


```
my iptables AFTER the router goes live 
```
  

sudo iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  localhost            anywhere             tcpflags:! FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  localhost            anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere             limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.5.255       
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere             state INVALID
LSI        all  -f  anywhere             anywhere             limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level info prefix "Unknown Input"

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere             limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level info prefix "Unknown Forward"

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  Dexter.local         localhost            tcp dpt:domain
ACCEPT     udp  --  Dexter.local         localhost            udp dpt:domain
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere             state INVALID
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level info prefix "Unknown Output"

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere             state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix "Inbound "
DROP       tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix "Inbound "
DROP       tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere             icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix "Inbound "
DROP       icmp --  anywhere             anywhere             icmp echo-request
LOG        all  --  anywhere             anywhere             limit: avg 5/sec burst 5 LOG level info prefix "Inbound "
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             limit: avg 5/sec burst 5 LOG level info prefix "Outbound "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere


```
thanks

---

### Post by albandy on 2012-11-05
When you say a router what exactly do you mean: A router or a switch? 

Also can you flush iptables? It can be easier to find the problem if no iptables are loaded.

---

### Post by JKyleOKC on 2012-11-05
If your only action between those two iptables listings was to bring up the router, then obviously there has to be something triggered by that action that makes all those changes to your iptables rules.

The output of the --list option is horribly ambiguous at best; as you can see it looks as if several rules duplicate each other. Try "sudo iptables -n -L" instead; the -n gives you numeric values instead of "anywhere" and the like, and the -L (case is important) is the same as --list.

However that still won't show how the list is getting changed. Are you perhaps using the /etc/network/interfaces file to configure your NIC interfaces? If you are, look for an "ip-up" script associated with eth2. If you aren't, check the /etc/NetworkManager directory and its subdirectories for anything similar. You may also find "ip-pre-up" or "ip-post-up" scripts. If you do find such a script, examine it for any references to "iptables" and if you find any, rename the script so that it cannot execute automatically.

Does any of this help, or even change the situation?

EDIT: Don't delete anything you find; just rename it, because you may find it necessary to put it back if something else breaks as a result!

---

### Post by pqwoerituytrueiwoq on 2012-11-05
so you are sharing your net with other systems
i did this before, this was my rc.local script
eth1 has Internet access eth1:1 is where the other system get there Internet connectin
```
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do
    sleep 1
done
while [ "`ifconfig eth1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
done
while [ "`ifconfig eth1:1 | grep 'inet addr:'`" = "" ]; do
    sleep 2 # create virtual nic
    ifconfig eth1:1 10.0.0.1 netmask 255.255.0.0
done
#iptables -t nat -A PREROUTING -o eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.75:80
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -P FORWARD ACCEPT
service dhcp3-server start
#ifconfig eth1:2 192.168.100.2 netmask 255.255.255.0
#notify-send --icon=info "Other computers can now use the Internet"
exit 0
```
i used this in my dhcpd.conf
```
shared-network 224-29 {
    subnet 10.0.0.0 netmask 255.255.0.0 {
        range 10.0.0.100 10.0.0.199;
        option routers 10.0.0.1;
        option domain-name-servers 8.8.8.8,8.8.4.4;
    }
}
host dhcp-server { # do not assign own ip address
   hardware ethernet 00:0a:cd:16:52:f6 ;
   deny booting ;
}
```

---

