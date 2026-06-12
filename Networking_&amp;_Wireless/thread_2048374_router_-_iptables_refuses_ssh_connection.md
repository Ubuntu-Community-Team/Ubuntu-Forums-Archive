---
title: "router - iptables refuses ssh connection"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by SeaKing on 2012-08-26
Hey,

I'm currently updating my router and there seems to be a problem with the iptables rules.
Current config:

DSL Modem -> Lan1 ->Router -> Lan2

When I try to connect from Lan2  to the Router everything's fine but if I try to connect from Lan1 to the router I get:
```
ssh: connect to host 192.168.0.15 port 22: No route to host
```but I can ping the router from Lan1 and everything's fine from Lan2.

Script:
```
[INDENT]# External (Internet-facing) interface
EXTIF=”eth0&#8243;
 # External IP address (automatically detected)
EXTIP=$(/sbin/ip addr show dev “$EXTIF” | perl -lne ‘if(/inet (\S+)/){print$1;last}’);
 # Internal interface
INTIF=”br0&#8243;
 # Internal IP address (in CIDR notation)
INTIP=”192.168.1.1/32&#8243;
 # Internal network address (in CIDR notation)
INTNET=”192.168.1.0/24&#8243;
 # The address of anything/everything (in CIDR notation)
UNIVERSE=”0.0.0.0/0&#8243;
 echo “External: [Interface=$EXTIF] [IP=$EXTIP]”
echo “Internal: [Interface=$INTIF] [IP=$INTIP] [Network:$INTNET]”
 echo
echo -n “Loading rules…”
 # Enabling IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward
 /sbin/iptables-restore <<-EOF;
 *filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
 ###################################################
# INPUT: Incoming traffic from various interfaces #
###################################################
 # Loopback interface is valid
-A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
 # Local interface, local machines, going anywhere is valid
-A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT
 # Remote interface, claiming to be local machines, IP spoofing, get lost
-A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j REJECT
 # External interface, from any source, for ICMP traffic is valid
-A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
 # Allow any related traffic coming back to the MASQ server in.
-A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m conntrack –ctstate ESTABLISHED,RELATED -j ACCEPT
 # Internal interface, DHCP traffic accepted
-A INPUT -i $INTIF -p tcp –sport 68 –dport 67 -j ACCEPT
-A INPUT -i $INTIF -p udp –sport 68 –dport 67 -j ACCEPT
 # Internal interface, DNS traffic accepted
-A INPUT -i $INTIF -p tcp –dport 53 -j ACCEPT
-A INPUT -i $INTIF -p udp –dport 53 -j ACCEPT
 # External interface, HTTP/HTTPS traffic allowed
-A INPUT -i $EXTIF -m conntrack –ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP –dport 80 -j ACCEPT
-A INPUT -i $EXTIF -m conntrack –ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP –dport 443 -j ACCEPT
 # External interface, SSH traffic allowed
-A INPUT -i $EXTIF -m conntrack –ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP –dport 22 -j ACCEPT
 # Accept port 1234 to be forwarded (this rule needs to correspond with PREROUTING rules in NAT table)
-A FORWARD -i $EXTIF -o $INTIF -p tcp –dport 1234 -m conntrack –ctstate NEW,ESTABLISHED,RELATED -j ACCEPT
 # Catch-all rule, reject anything else
-A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT
 ####################################################
# OUTPUT: Outgoing traffic from various interfaces #
####################################################
 # Workaround bug in netfilter
-A OUTPUT -m conntrack -p icmp –ctstate INVALID -j DROP
 # Loopback interface is valid.
-A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
 # Local interfaces, any source going to local net is valid
-A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT
 # local interface, MASQ server source going to the local net is valid
-A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT
 # outgoing to local net on remote interface, stuffed routing, deny
-A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j REJECT
 # anything else outgoing on remote interface is valid
-A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT
 # Internal interface, DHCP traffic accepted
-A OUTPUT -o $INTIF -p tcp -s $INTIP –sport 67 -d 255.255.255.255 –dport 68 -j ACCEPT
-A OUTPUT -o $INTIF -p udp -s $INTIP –sport 67 -d 255.255.255.255 –dport 68 -j ACCEPT
 # Internal interface, DNS traffic accepted
-A OUTPUT -o $INTIF -p tcp -s $INTIP –dport 53 -d 255.255.255.255 -j ACCEPT
-A OUTPUT -o $INTIF -p udp -s $INTIP –dport 53 -d 255.255.255.255 -j ACCEPT
 # Catch all rule, all other outgoing is denied and logged.
-A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT
 # Accept solicited tcp packets
-A FORWARD -i $EXTIF -o $INTIF -m conntrack –ctstate ESTABLISHED,RELATED  -j ACCEPT
 # Allow packets across the internal interface
-A FORWARD -i $INTIF -o $INTIF -j ACCEPT
 # Forward packets from the internal network to the Internet
-A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
 # Catch-all REJECT rule
-A FORWARD -j REJECT
 COMMIT
 ###########################
# Address translations (only; there is no actual forwarding done here)
###########################
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
 # —– Begin OPTIONAL FORWARD Section —–
 #Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#-A PREROUTING -p tcp -d $EXTIP –dport 1234 -m conntrack –ctstate NEW,ESTABLISHED,RELATED -j DNAT –to 192.168.0.100:1234
 # —– End OPTIONAL FORWARD Section —–
 # IP-Masquerade
-A POSTROUTING -o $EXTIF -j MASQUERADE
 COMMIT
EOF
 echo ” done.”
[/INDENT]
```

---

### Post by Doug S on 2012-08-26
I can not see a problem in your iptables rule set with respect to an external ssh (Lan 1). I'm not saying there isn't a problem, just that I don't see it.
I would do further tests and use the byte/packet counters to try to follow the packet paths through the rule set:```
sudo iptables -L -n -x -v
```Also, if you use a packet sniffer, such as tcpdump or tshark, use it to see if any packets actually arrive. Some debug logging rules might also help. There is a similar rule for HTTP and HTTPS traffic. Do you have a web server running, and does it work for Lan1 accesses?

---

### Post by SeaKing on 2012-08-27
the output:
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      97    20233 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
   11068   707641 ACCEPT     all  --  br0    *       192.168.1.0/24       0.0.0.0/0           
       0        0 REJECT     all  --  eth0   *       192.168.1.0/24       0.0.0.0/0           reject-with icmp-port-unreachable 
       5      420 ACCEPT     icmp --  eth0   *       0.0.0.0/0            192.168.0.0/24      
   24615 34948490 ACCEPT     all  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  br0    *       0.0.0.0/0            0.0.0.0/0           tcp spt:68 dpt:67 
       3      984 ACCEPT     udp  --  br0    *       0.0.0.0/0            0.0.0.0/0           udp spt:68 dpt:67 
       0        0 ACCEPT     tcp  --  br0    *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
       0        0 ACCEPT     udp  --  br0    *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate NEW,RELATED,ESTABLISHED tcp dpt:80 
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate NEW,RELATED,ESTABLISHED tcp dpt:443 
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate NEW,RELATED,ESTABLISHED tcp dpt:22 
     289    24309 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           tcp dpt:1234 ctstate NEW,RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           tcp dpt:22 ctstate NEW,RELATED,ESTABLISHED 
       0        0 ACCEPT     udp  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           udp dpt:22 ctstate NEW,RELATED,ESTABLISHED 
  620097 920026855 ACCEPT     all  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED 
     364    57394 ACCEPT     all  --  br0    br0     0.0.0.0/0            0.0.0.0/0           
  286813 16288404 ACCEPT     all  --  br0    eth0    0.0.0.0/0            0.0.0.0/0           
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate INVALID 
      97    20233 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  *      br0     192.168.0.0/24       192.168.1.0/24      
   11833  1934319 ACCEPT     all  --  *      br0     192.168.1.1          192.168.1.0/24      
       0        0 REJECT     all  --  *      eth0    0.0.0.0/0            192.168.1.0/24      reject-with icmp-port-unreachable 
   13589   752599 ACCEPT     all  --  *      eth0    192.168.0.0/24       0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      br0     192.168.1.1          255.255.255.255     tcp spt:67 dpt:68 
       0        0 ACCEPT     udp  --  *      br0     192.168.1.1          255.255.255.255     udp spt:67 dpt:68 
       0        0 ACCEPT     tcp  --  *      br0     192.168.1.1          255.255.255.255     tcp dpt:53 
       0        0 ACCEPT     udp  --  *      br0     192.168.1.1          255.255.255.255     udp dpt:53 
      40     3520 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
root@voyage:/etc/ssh# iptables -L -n -x -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      97    20233 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
   11100   709529 ACCEPT     all  --  br0    *       192.168.1.0/24       0.0.0.0/0           
       0        0 REJECT     all  --  eth0   *       192.168.1.0/24       0.0.0.0/0           reject-with icmp-port-unreachable 
       5      420 ACCEPT     icmp --  eth0   *       0.0.0.0/0            192.168.0.0/24      
   24615 34948490 ACCEPT     all  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  br0    *       0.0.0.0/0            0.0.0.0/0           tcp spt:68 dpt:67 
       3      984 ACCEPT     udp  --  br0    *       0.0.0.0/0            0.0.0.0/0           udp spt:68 dpt:67 
       0        0 ACCEPT     tcp  --  br0    *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
       0        0 ACCEPT     udp  --  br0    *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate NEW,RELATED,ESTABLISHED tcp dpt:80 
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate NEW,RELATED,ESTABLISHED tcp dpt:443 
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.0.0/24      ctstate NEW,RELATED,ESTABLISHED tcp dpt:22 
     289    24309 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           tcp dpt:1234 ctstate NEW,RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           tcp dpt:22 ctstate NEW,RELATED,ESTABLISHED 
       0        0 ACCEPT     udp  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           udp dpt:22 ctstate NEW,RELATED,ESTABLISHED 
  620101 920027516 ACCEPT     all  --  eth0   br0     0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED 
     364    57394 ACCEPT     all  --  br0    br0     0.0.0.0/0            0.0.0.0/0           
  286816 16290536 ACCEPT     all  --  br0    eth0    0.0.0.0/0            0.0.0.0/0           
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate INVALID 
      97    20233 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  *      br0     192.168.0.0/24       192.168.1.0/24      
   11864  1941387 ACCEPT     all  --  *      br0     192.168.1.1          192.168.1.0/24      
       0        0 REJECT     all  --  *      eth0    0.0.0.0/0            192.168.1.0/24      reject-with icmp-port-unreachable 
   13589   752599 ACCEPT     all  --  *      eth0    192.168.0.0/24       0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      br0     192.168.1.1          255.255.255.255     tcp spt:67 dpt:68 
       0        0 ACCEPT     udp  --  *      br0     192.168.1.1          255.255.255.255     udp spt:67 dpt:68 
       0        0 ACCEPT     tcp  --  *      br0     192.168.1.1          255.255.255.255     tcp dpt:53 
       0        0 ACCEPT     udp  --  *      br0     192.168.1.1          255.255.255.255     udp dpt:53 
      40     3520 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

```I also added these 2 lines in my rules script:
```
-A PREROUTING -p tcp -d $EXTIP --dport 22 -m conntrack --ctstate NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.1.1:22
-A PREROUTING -p udp -d $EXTIP --dport 22 -m conntrack --ctstate NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.1.1:22
```and now I get a time out error when connection from Lan1. Further there is currently no apache sever in Lan2 to check.

---

### Post by Doug S on 2012-08-27
In my opinion, it does not make any sense to add those two rules to your iptables rule set.
 
The line that automatically determines your external ip address seems to actually determine the external sub-net. For a test try hard coding it to what is actually is, 192.168.0.0 (or 192.168.0.0/32 if you prefer) (it isn't clear to me that you might not encounter some grief (confusion between networks and individual hosts) using 192.168.0.0 instead of, say, 192.168.0.1, but I have gotten lost in my text books and decided to post this reply before knowing for sure.) 
 
Between your two listings I assume that you tried a few times to connect from a computer on Lan1 to your linux box router via SSH (i.e. "ssh 192.168.0.0"). The packet count for that path remains at 0, which I guess we already know because it isn't working. I am wondering if the external ip being a sub-net instead of an actual single address is somehow causing the packets to take some other path. Although it remains unclear to me which other path. Based on the packet counters, there are only a couple of possibilities.
 
Is your DSL modem actually a DSL modem/router? I assumed it is. Did it assign the linux box the 192.168.0.0 address? Or did you assign it?
 
Edit: I see that the linux box is supposed to be at 192.168.0.15. Try hardcoding that. It is not clear to me how your brdige stuff is setup. I am used to two NIC cards to provide the Lan1 to Lan2 router stuff.

---

### Post by SeaKing on 2012-08-28
well the "external"  IP is already fixed to 192.168.0.15 and the bridge is between eth1 and wlan0. Additional ics-dhcp-server, bind9 and hostapd is running without problems.
And why should the 2 rules make no sense? Without them I let ssh traffic pass through but without any destination.

---

### Post by Doug S on 2012-08-28
Isn't the destination for SSH traffic the linux server itself? Then SSH packets should be picked up in the INPUT chain, with the rule that you have there.
 
The iptables rule set is determining the EXTIP as a network instead of a single host. Yes, I had a mistake in my previous posting because iptables lists it in its simplist form, which doesn't agree with what was listed from the command. Example part 1:```
doug@s15:~/temp_iptables$ /sbin/ip addr show dev eth0 | perl -lne 'if(/inet (\S+)/){print$1;last}'
[COLOR=red]192.168.111.112/24[/COLOR]
```Example part 2:```
doug@s15:~/temp_iptables$ cat test1
#! /bin/bash
#############################################
# iptables location
#
IPT=/sbin/iptables
#############################################
# Flush all current rules from iptables
#
$IPT -A INPUT -i eth0 -s 0.0.0.0/0 -d [COLOR=red]192.168.111.112/24[/COLOR] -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```Example part 3:```
doug@s15:~/temp_iptables$ sudo iptables -L -n -x -v
Chain INPUT (policy ACCEPT 3 packets, 234 bytes)
    pkts      bytes target     prot opt in     out     source               destination
... some stuff deleted...
      17      992 ACCEPT     all  --  eth0   *       0.0.0.0/0            [COLOR=red]192.168.111.0/24[/COLOR]     ctstate RELATED,ESTABLISHED
```I'm saying that perhaps the EXTIP should be a single address and not a sub-net.

---

### Post by Doug S on 2012-08-28
I made a script just like yours, but for my test computer. I could not get it not to work for an external SSH connection, for either way of decarling the EXTIP, and I could see the appropriate packet counters change as expected. I also have a web server on the test computer, and could see those packet counters behave as expected also.```
doug@s15:~/temp_iptables$ [COLOR=red]sudo iptables-save -c[/COLOR]
# Generated by iptables-save v1.4.12 on Tue Aug 28 12:25:51 2012
*nat
:PREROUTING ACCEPT [12:997]
:INPUT ACCEPT [3:144]
:OUTPUT ACCEPT [2:148]
:POSTROUTING ACCEPT [2:148]
[0:0] -A POSTROUTING -o eth0 -j MASQUERADE
COMMIT
# Completed on Tue Aug 28 12:25:51 2012
# Generated by iptables-save v1.4.12 on Tue Aug 28 12:25:51 2012
*mangle
:PREROUTING ACCEPT [138:12262]
:INPUT ACCEPT [138:12262]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [123:28822]
:POSTROUTING ACCEPT [121:28314]
COMMIT
# Completed on Tue Aug 28 12:25:51 2012
# Generated by iptables-save v1.4.12 on Tue Aug 28 12:25:51 2012
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
[4:450] -A INPUT -i lo -j ACCEPT
[0:0] -A INPUT -s 192.168.222.0/24 -i eth1 -j ACCEPT
[0:0] -A INPUT -s 192.168.222.0/24 -i eth0 -j REJECT --reject-with icmp-port-unreachable
[0:0] -A INPUT -d 192.168.111.0/24 -i eth0 -p icmp -j ACCEPT
[122:10815] -A INPUT -d 192.168.111.0/24 -i eth0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
[0:0] -A INPUT -i eth1 -p tcp -m tcp --sport 68 --dport 67 -j ACCEPT
[0:0] -A INPUT -i eth1 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
[0:0] -A INPUT -i eth1 -p tcp -m tcp --dport 53 -j ACCEPT
[0:0] -A INPUT -i eth1 -p udp -m udp --dport 53 -j ACCEPT
[COLOR=red][1:48] -A INPUT -d 192.168.111.0/24 -i eth0 -p tcp -m conntrack --ctstate NEW,RELATED,ESTABLISHED -m tcp --dport 80 -j ACCEPT[/COLOR]
[0:0] -A INPUT -d 192.168.111.0/24 -i eth0 -p tcp -m conntrack --ctstate NEW,RELATED,ESTABLISHED -m tcp --dport 443 -j ACCEPT
[COLOR=red][2:96] -A INPUT -d 192.168.111.0/24 -i eth0 -p tcp -m conntrack --ctstate NEW,RELATED,ESTABLISHED -m tcp --dport 22 -j ACCEPT[/COLOR]
[9:853] -A INPUT -j REJECT --reject-with icmp-port-unreachable
[0:0] -A FORWARD -i eth0 -o eth1 -p tcp -m tcp --dport 1234 -m conntrack --ctstate NEW,RELATED,ESTABLISHED -j ACCEPT
[0:0] -A FORWARD -i eth0 -o eth1 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
[0:0] -A FORWARD -i eth1 -o eth1 -j ACCEPT
[0:0] -A FORWARD -i eth1 -o eth0 -j ACCEPT
[0:0] -A FORWARD -j REJECT --reject-with icmp-port-unreachable
[0:0] -A OUTPUT -p icmp -m conntrack --ctstate INVALID -j DROP
[4:450] -A OUTPUT -o lo -j ACCEPT
[0:0] -A OUTPUT -s 192.168.111.0/24 -d 192.168.222.0/24 -o eth1 -j ACCEPT
[0:0] -A OUTPUT -s 192.168.222.1/32 -d 192.168.222.0/24 -o eth1 -j ACCEPT
[0:0] -A OUTPUT -d 192.168.222.0/24 -o eth0 -j REJECT --reject-with icmp-port-unreachable
[117:27864] -A OUTPUT -s 192.168.111.0/24 -o eth0 -j ACCEPT
[0:0] -A OUTPUT -s 192.168.222.1/32 -d 255.255.255.255/32 -o eth1 -p tcp -m tcp --sport 67 --dport 68 -j ACCEPT
[0:0] -A OUTPUT -s 192.168.222.1/32 -d 255.255.255.255/32 -o eth1 -p udp -m udp --sport 67 --dport 68 -j ACCEPT
[0:0] -A OUTPUT -s 192.168.222.1/32 -d 255.255.255.255/32 -o eth1 -p tcp -m tcp --dport 53 -j ACCEPT
[0:0] -A OUTPUT -s 192.168.222.1/32 -d 255.255.255.255/32 -o eth1 -p udp -m udp --dport 53 -j ACCEPT
[0:0] -A OUTPUT -j REJECT --reject-with icmp-port-unreachable
COMMIT
# Completed on Tue Aug 28 12:25:51 2012
doug@s15:~/temp_iptables$
```I did each of these lines in my script:```
EXTIF="eth0"
 # External IP address (automatically detected)
#EXTIP="192.168.111.112"
EXTIP=$(/sbin/ip addr show dev "$EXTIF" | perl -lne 'if(/inet (\S+)/){print$1;last}');

```I am out of ideas.

---

### Post by SeaKing on 2012-09-02
Solution found. 
First: sorry for late reply 
Second: I kept the prerouting rule to 192.168.1.1 AND I added in /etc/ssh/sshd.conf:
ListenAddress 192.168.1.1.  //LAN2 Address
ListenAddress 192.168.0.15 //LAN1 Address
ListenAddress 127.0.0.1        //Localhost , no idea if it's necessary but I put it in
now I can access the router from both sites

---

### Post by Doug S on 2012-09-03
Thanks for reporting back, and glad you got it working.
It is not clear to me why you had to add the specific ListenAddress directives, by default sshd should listen on all local addresses. I do not have any ListenAddress directives in my sshd_config file.

---

