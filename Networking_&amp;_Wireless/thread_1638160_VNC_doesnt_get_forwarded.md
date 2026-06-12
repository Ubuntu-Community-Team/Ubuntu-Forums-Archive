---
title: "VNC doesnt get forwarded"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by koszta on 2010-12-05
Hi, 
I cant get my ubuntu machine to forward my vnc - I cant log on my windows machine running the server (it is DMZ and its ip is 192.168.1.2)

Here is my firewall dump? What am I doing wrong? The important parts are connection sharing and forward allowance..

```
#!/bin/bash
ipt=/sbin/iptables

#define interfaces
wan=eth0
dmz=eth2
lan=eth1
echo "setting up firewall variables"
echo "flushing tables"
#flush all tables
$ipt -F
echo "setting up default policies"
#set default policy
$ipt -P INPUT DROP
$ipt -P FORWARD DROP
$ipt -P OUTPUT ACCEPT
$ipt -t nat -P OUTPUT ACCEPT
$ipt -t nat -P PREROUTING ACCEPT
$ipt -t nat -P POSTROUTING ACCEPT
$ipt -t mangle -P PREROUTING ACCEPT
$ipt -t mangle -P POSTROUTING ACCEPT

#aceept all loopback traffic
$ipt -A INPUT -i lo -j ACCEPT

# accept ICMP
$ipt -A INPUT -p icmp --icmp-type echo-reply -m state --state ESTABLISHED,RELATED -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type echo-request -m limit --limit 5/s -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type destination-unreachable -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type time-exceeded -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type timestamp-request -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type timestamp-reply -m state --state ESTABLISHED,RELATED -j ACCEPT


echo "setting up stateful firewall"
#stateful firewall basic rule
$ipt -A INPUT -i $wan -m state --state ESTABLISHED,RELATED -j ACCEPT
$ipt -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
echo "setting up interfaces policy"
#################################################
#          interfaces settings                  #
#################################################
echo "allowing services"
$ipt -A INPUT -i $dmz -j ACCEPT
#################################################		
#	outside service allowance		#
#################################################
#ssh from Inet allowance 
$ipt -A INPUT -i $wan -p tcp --dport 22 --sport 1024:65535 -m state --state NEW -j ACCEPT
#allow mysql remote login
$ipt -A INPUT -i $wan -p tcp --dport 3306 --sport 1024:65535 -m state --state NEW -j ACCEPT
# allow VNC
$ipt -I INPUT -i $wan -p tcp -m state --state NEW --dport 5900 -j ACCEPT

#################################################               
#       inside service allowance                #
#################################################
# allow LAN dhcp requests
$ipt  -I INPUT -i $lan -p udp --dport 68 --sport 67 -j ACCEPT
# allow DMZ dhcp requests
$ipt  -I INPUT -i $dmz -p udp --dport 68 --sport 67 -j ACCEPT
#################################################
#       connection sharing                      #
#################################################
$ipt -A FORWARD -o $wan -s 192.168.1.2  -j ACCEPT
$ipt -A FORWARD -d 192.168.1.2 -m state --state ESTABLISHED,RELATED -i $wan -j ACCEPT

#enable masquarade 
$ipt -t nat -A POSTROUTING -o $wan -j SNAT --to OUTSIDEIP
# prerouting
$ipt -t nat -A PREROUTING -i $wan -p tcp --dport 5900 --sport 1024:65535 -j DNAT --to 192.168.1.2:5900
#################################################
#       forward allowance                       #
#################################################
$ipt -A FORWARD -p tcp -i $wan -o $dmz --dport 5900 -d 192.168.1.2 -j ACCEPT
#THIS LINE SHOULD DO THE TRICK....WHY ISNT IT WORKING


#################################################               
#       defend server against typical attacks   #
#################################################

#make sure new packets have syn flag 
$ipt -A INPUT -p tcp ! --syn -m state --state NEW -j DROP

echo "FIREWALL UP!!!"
echo "//tip -> run \"netstat --inet -an\" for list of opened ports"
```

I just dont know what to do and I am going crazy ... thanks

---

### Post by koszta on 2010-12-08
there is apparently a windows7 and vista bug on real vnc that caused mu problem. 

If anybody has a similar problem here is a solution:
[http://www.mydigitallife.info/2006/12/13/workaround-to-run-vnc-server-in-windows-vista/](http://www.mydigitallife.info/2006/12/13/workaround-to-run-vnc-server-in-windows-vista/)

---

