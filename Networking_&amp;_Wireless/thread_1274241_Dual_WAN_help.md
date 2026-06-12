---
title: "Dual WAN help"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by iLLNiSS on 2009-09-24
I tried searching but couldnt really find anything useful for me. Sorry if i missed something but i'm fairly new to ubuntu.
 
So here's the lowdown. I've got an old PC in the basement i use as a dedicated file server and sabnzbd server. It's got an onboard NIC that I do not use, and a 1GBit NIC that i use for the networking.
 
The 1Gbit NIC is connected to my router which networks the computer to an HTPC/etc. I have a 15Mbps cable modem attached to the router. This router again serves all my networking between the server and computers on the network as well as provides internet to all those devices.
 
What I'm looking to do is add a second internet connection to my onboard NIC to be used strictly for the server, and not for the router. So the server will see dual WAN but the network will only see one connection. I'm not worried about load balancing or anything fancy. So the server itself will not do any routing for the network just for itself.
 
Anyone have any pointers on where to start? What software to use? etc..

---

### Post by Lars Noodén on 2009-09-24
The tools at the bottom of it all would be iptables and brctl.  That by itself is not much help, but might point you in the right direction.  

If you get it set up, it would be nice to have a follow up post here or elsewhere showing how you did it.

---

### Post by superprash2003 on 2009-09-24
im not sure if this is what you mean  [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by iLLNiSS on 2009-09-30
well ive only managed to go as far as getting redundancy on my ubuntu with two wans

ive followed a dual wan guide for ubuntu that appearantly load balances, but it doesn't seem to do that.

when im downloading it always favors eth0. the only time eth1 kicks on is when eth0 is disconnected.

no one here has a foolproof way of getting dual wan (double the download speed with multiple threads) setup on ubuntu?

---

### Post by jbarbieri on 2009-10-19
I will try and make this as easy as possible. I have this running on my ubuntu router at home.  eth1 is my LAN adapter, and eth0 and eth2 are my 2 public adapters.


First, I made a file in /etc/init.d and named it firewall, and it contained the following: 

```

#!/bin/sh -e

case "$1" in
  start)
       ifconfig eth1 10.10.100.2 netmask 255.255.255.0 up
       ifconfig eth0 up
       ifconfig eth2 up
       /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf eth1
       dhclient -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases -sf /root/wan1script eth0
       dhclient -pf /var/run/dhclient.eth2.pid -lf /var/lib/dhcp3/dhclient.eth2.leases -sf /root/wan2.script eth2
       ifconfig eth0 mtu 1500
       ifconfig eth1 mtu 1500
       ifconfig eth2 mtu 1500
       /root/routes.firewall
       iptables -F
       iptables -F -t nat
       iptables -F -t mangle
       /root/firewall.firewall
       /root/forwards.firewall
        ;;
  stop)
        ;;
  *)
        echo "Usage: {start|stop|restart|force-reload|status}" >&2
        exit 1
        ;;
esac

exit 0

```
I made symlinks in the appropriate folders so that this script will launch when booted.

The following are the two scripts for DHClient (wan1.script and wan2.script)

wan1.script
```

#!/bin/sh
RUN="yes"
if [ "$RUN" = "yes" ]; then
echo $new_ip_address > /root/tmp/wan1.ip
echo $new_subnet_mask > /root/tmp/wan1.netmask
echo $new_routers > /root/tmp/wan1.router
echo $interface > /root/tmp/wan1.iface
echo $new_broadcast_address > /root/tmp/wan1.broadcast

ifconfig $interface $new_ip_address netmask $new_subnet_mask mtu 1500 up

fi

```wan2.script
```

#!/bin/sh
RUN="yes"
if [ "$RUN" = "yes" ]; then
echo $new_ip_address > /root/tmp/wan2.ip
echo $new_subnet_mask > /root/tmp/wan2.netmask
echo $new_routers > /root/tmp/wan2.router
echo $interface > /root/tmp/wan2.iface

ifconfig $interface $new_ip_address netmask $new_subnet_mask mtu 1500 up
fi

```These 2 scripts configure the interfaces, and stores values into /root/tmp that other scripts will call.


The routes.firewall looks like this:

```

#!/bin/sh

wan1=`cat /root/tmp/wan1.ip`
wan2=`cat /root/tmp/wan2.ip`
wan1mask=`cat /root/tmp/wan1.netmask`
wan2mask=`cat /root/tmp/wan2.netmask`
wan1router=`cat /root/tmp/wan1.router`
wan2router=`cat /root/tmp/wan2.router`
wan1iface=`cat /root/tmp/wan1.iface`
wan2iface=`cat /root/tmp/wan2.iface`

echo "Flushing rules" >> /var/log/messages

ip rule flush

echo "Rebuilding rules and tables" >> /var/log/messages
echo "$wan1 $wan2 $wan1mask $wan2mask $wan1router $wan2router $wan1iface $wan2iface" >> /var/log/messages

ip rule add lookup main prio 32766
ip rule add lookup default prio 32767

ip rule add from $wan1 table 100 prio 100
ip rule add fwmark 0x100 table 100 prio 101

ip rule add from $wan2 table 200 prio 200
ip rule add fwmark 0x200 table 200 prio 201

ip route flush table 100
ip route flush table 200

for TABLE in 100 200
do
   ip route | grep link | while read ROUTE
   do
     ip route add table $TABLE to $ROUTE
   done
done

ip route add table 100 default via $wan1router
ip route add table 200 default via $wan2router
echo "Deleting default route" >> /var/log/messages
ip route delete default
echo "Adding in equalized route" >> /var/log/messages
ip route add default scope global equalize nexthop via $wan1router dev $wan1iface nexthop via $wan2router dev $wan2iface
echo "routes.firewall completed" >> /var/log/messages

```
firewall.firewall looks like this
```

#!/bin/sh
wan1=`cat /root/tmp/wan1.ip`
wan2=`cat /root/tmp/wan2.ip`
wan1mask=`cat /root/tmp/wan1.netmask`
wan2mask=`cat /root/tmp/wan2.netmask`
wan1router=`cat /root/tmp/wan1.router`
wan2router=`cat /root/tmp/wan2.router`
wan1iface=`cat /root/tmp/wan1.iface`
wan2iface=`cat /root/tmp/wan2.iface`
laniface=eth1

echo "`date` Flushing and adding new firewall rules" >> /var/log/messages
IPTABLES="/sbin/iptables"

$IPTABLES -t mangle -F PREROUTING
$IPTABLES -t mangle -F OUTPUT

$IPTABLES -F POSTROUTING -t nat

$IPTABLES -t mangle -N ETH1
$IPTABLES -t mangle -F ETH1
$IPTABLES -t mangle -A ETH1 -j MARK --set-mark 0x100
$IPTABLES -t mangle -A ETH1 -j CONNMARK --save-mark

$IPTABLES -t mangle -N ETH2
$IPTABLES -t mangle -F ETH2
$IPTABLES -t mangle -A ETH2 -j MARK --set-mark 0x200
$IPTABLES -t mangle -A ETH2 -j CONNMARK --save-mark

$IPTABLES -t mangle -N RANDOM
$IPTABLES -t mangle -F RANDOM
$IPTABLES -t mangle -A RANDOM -m statistic --mode random --probability .5 -j ETH1
$IPTABLES -t mangle -A RANDOM -m statistic --mode random --probability .5 -j ETH2

$IPTABLES -t filter -N UPNP
$IPTABLES -t filter -F UPNP

$IPTABLES -t nat -N SPOOF_ETH1
$IPTABLES -t nat -F SPOOF_ETH1
$IPTABLES -t nat -A SPOOF_ETH1 -j SNAT --to $wan1
$IPTABLES -t nat -N SPOOF_ETH2
$IPTABLES -t nat -F SPOOF_ETH2
$IPTABLES -t nat -A SPOOF_ETH2 -j SNAT --to $wan2

$IPTABLES -t filter -N keep_state
$IPTABLES -t filter -A keep_state -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -t filter -A keep_state -j RETURN

$IPTABLES -t nat -N keep_state
$IPTABLES -t nat -A keep_state -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -t nat -A keep_state -j RETURN

$IPTABLES -t nat -I PREROUTING -j keep_state
$IPTABLES -t nat -I OUTPUT -j keep_state
$IPTABLES -t filter -I INPUT -j keep_state
$IPTABLES -t filter -I FORWARD -j keep_state
$IPTABLES -t filter -I OUTPUT -j keep_state

$IPTABLES -t filter -I INPUT -i $laniface -m state --state NEW -j ACCEPT
$IPTABLES -t filter -I FORWARD -i $laniface -m state --state NEW -j ACCEPT

$IPTABLES -t filter -I FORWARD -j UPNP

$IPTABLES -t nat -I POSTROUTING -j keep_state
$IPTABLES -t nat -A POSTROUTING -o $wan1iface -j SPOOF_ETH1
$IPTABLES -t nat -A POSTROUTING -o $wan2iface -j SPOOF_ETH2

$IPTABLES -t mangle -A FORWARD -j CONNMARK --restore-mark
$IPTABLES -t mangle -A FORWARD -i $wan1iface -j ETH1
$IPTABLES -t mangle -A FORWARD -i $wan2iface -j ETH2
$IPTABLES -t mangle -A PREROUTING -i $laniface -p tcp -m state --state ESTABLISHED -j CONNMARK --restore-mark
$IPTABLES -t mangle -A PREROUTING -i $laniface -m state --state NEW -j RANDOM
$IPTABLES -t mangle -A PREROUTING -m mark --mark 0x100 -j ACCEPT
$IPTABLES -t mangle -A PREROUTING -m mark --mark 0x200 -j ACCEPT
$IPTABLES -t mangle -A PREROUTING -i $wan1iface -j ETH1
$IPTABLES -t mangle -A PREROUTING -i $wan2iface -j ETH2

# Rate Limit
$IPTABLES -N rate_limit
$IPTABLES -F rate_limit
$IPTABLES -A rate_limit -p tcp --dport 22 -m limit --limit 3/min --limit-burst 3 -j ACCEPT
$IPTABLES -A rate_limit -p udp --dport 1194 -m limit --limit 3/min --limit-burst 3 -j ACCEPT
$IPTABLES -A rate_limit -p ICMP --icmp-type echo-request -m limit --limit 3/sec -j ACCEPT
$IPTABLES -A rate_limit -p ! ICMP -j LOG --log-prefix " Connection dropped!! "
$IPTABLES -A rate_limit -p tcp -j REJECT --reject-with tcp-reset
$IPTABLES -A rate_limit -p udp -j REJECT --reject-with icmp-port-unreachable
$IPTABLES -A rate_limit -j DROP

# Add Limits
$IPTABLES -I INPUT -p ICMP --icmp-type echo-request -j rate_limit
$IPTABLES -I INPUT -p tcp --dport 22 -m state --state NEW -j rate_limit

RP_PATH=/proc/sys/net/ipv4/conf
for IFACE in `ls $RP_PATH`; do
    echo 0 > $RP_PATH/$IFACE/rp_filter
done

echo "`date` firewall.firewall is now completed" >> /var/log/messages

```
and forwards.firewall are where I put some port-forwarding rules in
```

#!/bin/sh
wan1=`cat /root/tmp/wan1.ip`
wan2=`cat /root/tmp/wan2.ip`
wan1mask=`cat /root/tmp/wan1.netmask`
wan2mask=`cat /root/tmp/wan2.netmask`
wan1router=`cat /root/tmp/wan1.router`
wan2router=`cat /root/tmp/wan2.router`
wan1iface=`cat /root/tmp/wan1.iface`
wan2iface=`cat /root/tmp/wan2.iface`
laniface=eth1
IPTABLES="/sbin/iptables"


echo "`date` Running forwards.firewall" >> /var/log/messages

$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -p udp --dport 161 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPT

$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,RST FIN,RST -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,ACK FIN -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags ACK,URG URG -j DROP

$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,RST FIN,RST -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,ACK FIN -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags ACK,URG URG -j DROP

## Drop the rest
$IPTABLES -t filter -A INPUT -j DROP

## Forwards
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan1 --dport 5600 -j DNAT --to 10.10.100.103:5901
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan2 --dport 5600 -j DNAT --to 10.10.100.103:5901
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan1 --dport 8000 -j DNAT --to 10.10.100.103:8000
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan2 --dport 8000 -j DNAT --to 10.10.100.103:8000
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan1 --dport 9001 -j DNAT --to 10.10.100.103:9001
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan2 --dport 9001 -j DNAT --to 10.10.100.103:9001
echo "`date` Finished running forwards.firewall" >> /var/log/messages

```

Need to change sysctl.conf to allow forwarding:

```

vi /etc/sysctl.conf
```

Look for: net.ipv4.ip_forward=0 and change to net.ipv4.ip_forward=1.


With all those set up, and of course, doing a chmod +x on the appropriate files, my router was now a dual WAN router. Last week, I made a little change, and it is now a triple WAN router, using 802.1Q tagging. This allows multiple external interfaces, but by using 802.1Q tagging, only 2 interfaces are needed on the router. You are not limited to how many ethernet ports are on the router at that point.

Hope the helps!

--John


Source: Loads of work I did here, then modified to run on Linux and not DD-WRT:  [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=13869](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=13869)

---

### Post by felizf on 2010-03-10
> **jbarbieri said:**
> I will try and make this as easy as possible. I have this running on my ubuntu router at home.  eth1 is my LAN adapter, and eth0 and eth2 are my 2 public adapters.


First, I made a file in /etc/init.d and named it firewall, and it contained the following: 

```

#!/bin/sh -e

case "$1" in
  start)
       ifconfig eth1 10.10.100.2 netmask 255.255.255.0 up
       ifconfig eth0 up
       ifconfig eth2 up
       /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf eth1
       dhclient -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases -sf /root/wan1script eth0
       dhclient -pf /var/run/dhclient.eth2.pid -lf /var/lib/dhcp3/dhclient.eth2.leases -sf /root/wan2.script eth2
       ifconfig eth0 mtu 1500
       ifconfig eth1 mtu 1500
       ifconfig eth2 mtu 1500
       /root/routes.firewall
       iptables -F
       iptables -F -t nat
       iptables -F -t mangle
       /root/firewall.firewall
       /root/forwards.firewall
        ;;
  stop)
        ;;
  *)
        echo "Usage: {start|stop|restart|force-reload|status}" >&2
        exit 1
        ;;
esac

exit 0

```
I made symlinks in the appropriate folders so that this script will launch when booted.

The following are the two scripts for DHClient (wan1.script and wan2.script)

wan1.script
```

#!/bin/sh
RUN="yes"
if [ "$RUN" = "yes" ]; then
echo $new_ip_address > /root/tmp/wan1.ip
echo $new_subnet_mask > /root/tmp/wan1.netmask
echo $new_routers > /root/tmp/wan1.router
echo $interface > /root/tmp/wan1.iface
echo $new_broadcast_address > /root/tmp/wan1.broadcast

ifconfig $interface $new_ip_address netmask $new_subnet_mask mtu 1500 up

fi

```wan2.script
```

#!/bin/sh
RUN="yes"
if [ "$RUN" = "yes" ]; then
echo $new_ip_address > /root/tmp/wan2.ip
echo $new_subnet_mask > /root/tmp/wan2.netmask
echo $new_routers > /root/tmp/wan2.router
echo $interface > /root/tmp/wan2.iface

ifconfig $interface $new_ip_address netmask $new_subnet_mask mtu 1500 up
fi

```These 2 scripts configure the interfaces, and stores values into /root/tmp that other scripts will call.


The routes.firewall looks like this:

```

#!/bin/sh

wan1=`cat /root/tmp/wan1.ip`
wan2=`cat /root/tmp/wan2.ip`
wan1mask=`cat /root/tmp/wan1.netmask`
wan2mask=`cat /root/tmp/wan2.netmask`
wan1router=`cat /root/tmp/wan1.router`
wan2router=`cat /root/tmp/wan2.router`
wan1iface=`cat /root/tmp/wan1.iface`
wan2iface=`cat /root/tmp/wan2.iface`

echo "Flushing rules" >> /var/log/messages

ip rule flush

echo "Rebuilding rules and tables" >> /var/log/messages
echo "$wan1 $wan2 $wan1mask $wan2mask $wan1router $wan2router $wan1iface $wan2iface" >> /var/log/messages

ip rule add lookup main prio 32766
ip rule add lookup default prio 32767

ip rule add from $wan1 table 100 prio 100
ip rule add fwmark 0x100 table 100 prio 101

ip rule add from $wan2 table 200 prio 200
ip rule add fwmark 0x200 table 200 prio 201

ip route flush table 100
ip route flush table 200

for TABLE in 100 200
do
   ip route | grep link | while read ROUTE
   do
     ip route add table $TABLE to $ROUTE
   done
done

ip route add table 100 default via $wan1router
ip route add table 200 default via $wan2router
echo "Deleting default route" >> /var/log/messages
ip route delete default
echo "Adding in equalized route" >> /var/log/messages
ip route add default scope global equalize nexthop via $wan1router dev $wan1iface nexthop via $wan2router dev $wan2iface
echo "routes.firewall completed" >> /var/log/messages

```
firewall.firewall looks like this
```

#!/bin/sh
wan1=`cat /root/tmp/wan1.ip`
wan2=`cat /root/tmp/wan2.ip`
wan1mask=`cat /root/tmp/wan1.netmask`
wan2mask=`cat /root/tmp/wan2.netmask`
wan1router=`cat /root/tmp/wan1.router`
wan2router=`cat /root/tmp/wan2.router`
wan1iface=`cat /root/tmp/wan1.iface`
wan2iface=`cat /root/tmp/wan2.iface`
laniface=eth1

echo "`date` Flushing and adding new firewall rules" >> /var/log/messages
IPTABLES="/sbin/iptables"

$IPTABLES -t mangle -F PREROUTING
$IPTABLES -t mangle -F OUTPUT

$IPTABLES -F POSTROUTING -t nat

$IPTABLES -t mangle -N ETH1
$IPTABLES -t mangle -F ETH1
$IPTABLES -t mangle -A ETH1 -j MARK --set-mark 0x100
$IPTABLES -t mangle -A ETH1 -j CONNMARK --save-mark

$IPTABLES -t mangle -N ETH2
$IPTABLES -t mangle -F ETH2
$IPTABLES -t mangle -A ETH2 -j MARK --set-mark 0x200
$IPTABLES -t mangle -A ETH2 -j CONNMARK --save-mark

$IPTABLES -t mangle -N RANDOM
$IPTABLES -t mangle -F RANDOM
$IPTABLES -t mangle -A RANDOM -m statistic --mode random --probability .5 -j ETH1
$IPTABLES -t mangle -A RANDOM -m statistic --mode random --probability .5 -j ETH2

$IPTABLES -t filter -N UPNP
$IPTABLES -t filter -F UPNP

$IPTABLES -t nat -N SPOOF_ETH1
$IPTABLES -t nat -F SPOOF_ETH1
$IPTABLES -t nat -A SPOOF_ETH1 -j SNAT --to $wan1
$IPTABLES -t nat -N SPOOF_ETH2
$IPTABLES -t nat -F SPOOF_ETH2
$IPTABLES -t nat -A SPOOF_ETH2 -j SNAT --to $wan2

$IPTABLES -t filter -N keep_state
$IPTABLES -t filter -A keep_state -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -t filter -A keep_state -j RETURN

$IPTABLES -t nat -N keep_state
$IPTABLES -t nat -A keep_state -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -t nat -A keep_state -j RETURN

$IPTABLES -t nat -I PREROUTING -j keep_state
$IPTABLES -t nat -I OUTPUT -j keep_state
$IPTABLES -t filter -I INPUT -j keep_state
$IPTABLES -t filter -I FORWARD -j keep_state
$IPTABLES -t filter -I OUTPUT -j keep_state

$IPTABLES -t filter -I INPUT -i $laniface -m state --state NEW -j ACCEPT
$IPTABLES -t filter -I FORWARD -i $laniface -m state --state NEW -j ACCEPT

$IPTABLES -t filter -I FORWARD -j UPNP

$IPTABLES -t nat -I POSTROUTING -j keep_state
$IPTABLES -t nat -A POSTROUTING -o $wan1iface -j SPOOF_ETH1
$IPTABLES -t nat -A POSTROUTING -o $wan2iface -j SPOOF_ETH2

$IPTABLES -t mangle -A FORWARD -j CONNMARK --restore-mark
$IPTABLES -t mangle -A FORWARD -i $wan1iface -j ETH1
$IPTABLES -t mangle -A FORWARD -i $wan2iface -j ETH2
$IPTABLES -t mangle -A PREROUTING -i $laniface -p tcp -m state --state ESTABLISHED -j CONNMARK --restore-mark
$IPTABLES -t mangle -A PREROUTING -i $laniface -m state --state NEW -j RANDOM
$IPTABLES -t mangle -A PREROUTING -m mark --mark 0x100 -j ACCEPT
$IPTABLES -t mangle -A PREROUTING -m mark --mark 0x200 -j ACCEPT
$IPTABLES -t mangle -A PREROUTING -i $wan1iface -j ETH1
$IPTABLES -t mangle -A PREROUTING -i $wan2iface -j ETH2

# Rate Limit
$IPTABLES -N rate_limit
$IPTABLES -F rate_limit
$IPTABLES -A rate_limit -p tcp --dport 22 -m limit --limit 3/min --limit-burst 3 -j ACCEPT
$IPTABLES -A rate_limit -p udp --dport 1194 -m limit --limit 3/min --limit-burst 3 -j ACCEPT
$IPTABLES -A rate_limit -p ICMP --icmp-type echo-request -m limit --limit 3/sec -j ACCEPT
$IPTABLES -A rate_limit -p ! ICMP -j LOG --log-prefix " Connection dropped!! "
$IPTABLES -A rate_limit -p tcp -j REJECT --reject-with tcp-reset
$IPTABLES -A rate_limit -p udp -j REJECT --reject-with icmp-port-unreachable
$IPTABLES -A rate_limit -j DROP

# Add Limits
$IPTABLES -I INPUT -p ICMP --icmp-type echo-request -j rate_limit
$IPTABLES -I INPUT -p tcp --dport 22 -m state --state NEW -j rate_limit

RP_PATH=/proc/sys/net/ipv4/conf
for IFACE in `ls $RP_PATH`; do
    echo 0 > $RP_PATH/$IFACE/rp_filter
done

echo "`date` firewall.firewall is now completed" >> /var/log/messages

```
and forwards.firewall are where I put some port-forwarding rules in
```

#!/bin/sh
wan1=`cat /root/tmp/wan1.ip`
wan2=`cat /root/tmp/wan2.ip`
wan1mask=`cat /root/tmp/wan1.netmask`
wan2mask=`cat /root/tmp/wan2.netmask`
wan1router=`cat /root/tmp/wan1.router`
wan2router=`cat /root/tmp/wan2.router`
wan1iface=`cat /root/tmp/wan1.iface`
wan2iface=`cat /root/tmp/wan2.iface`
laniface=eth1
IPTABLES="/sbin/iptables"


echo "`date` Running forwards.firewall" >> /var/log/messages

$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -p udp --dport 161 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPT

$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,RST FIN,RST -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags FIN,ACK FIN -j DROP
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --tcp-flags ACK,URG URG -j DROP

$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,RST FIN,RST -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags FIN,ACK FIN -j DROP
$IPTABLES -A INPUT -i eth2 -p tcp -m tcp --tcp-flags ACK,URG URG -j DROP

## Drop the rest
$IPTABLES -t filter -A INPUT -j DROP

## Forwards
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan1 --dport 5600 -j DNAT --to 10.10.100.103:5901
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan2 --dport 5600 -j DNAT --to 10.10.100.103:5901
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan1 --dport 8000 -j DNAT --to 10.10.100.103:8000
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan2 --dport 8000 -j DNAT --to 10.10.100.103:8000
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan1 --dport 9001 -j DNAT --to 10.10.100.103:9001
$IPTABLES -A PREROUTING -t nat -p tcp -d $wan2 --dport 9001 -j DNAT --to 10.10.100.103:9001
echo "`date` Finished running forwards.firewall" >> /var/log/messages

```

Need to change sysctl.conf to allow forwarding:

```

vi /etc/sysctl.conf
```

Look for: net.ipv4.ip_forward=0 and change to net.ipv4.ip_forward=1.


With all those set up, and of course, doing a chmod +x on the appropriate files, my router was now a dual WAN router. Last week, I made a little change, and it is now a triple WAN router, using 802.1Q tagging. This allows multiple external interfaces, but by using 802.1Q tagging, only 2 interfaces are needed on the router. You are not limited to how many ethernet ports are on the router at that point.

Hope the helps!

--John


Source: Loads of work I did here, then modified to run on Linux and not DD-WRT:  [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=13869](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=13869)

if it's not too much trouble, do you think you could modify all of this to make it work with a quad-wan set up? I've been searching for HOURS without any luck. I would HIGHLY appreciate it if you could! thanks!

---

### Post by jbarbieri on 2010-03-11
> **felizf said:**
> if it's not too much trouble, do you think you could modify all of this to make it work with a quad-wan set up? I've been searching for HOURS without any luck. I would HIGHLY appreciate it if you could! thanks!


Start with this:

[www.jbarbieri.net/dual_wan/quad.tar](www.jbarbieri.net/dual_wan/quad.tar)

Follow the readme and change your interfaces accordingly.

---

### Post by idman on 2010-06-18
Hello,

Could you provide us examples scripts regarding :

1. Force an LAN ip to SNAT only on specify WANif ; (eg. 10.10.100.20 -> out -> WAN2)

2. Force ports 21,22, 53, 80, 443 to use only WAN1 and rest (eg. torrents) to use load balancing (WAN3,WAN2,WAN1);

3. 3xMode support : Load Balancing, Fail-Over, Load-Balancing + Failover;
Note : I know that for fail-over we need a script for pinging all gw and switch the gateways.

Best regards,

---

### Post by jzlab.com on 2010-07-08
thx u 2!

now, i'll try to setup this ubuntu dualwan box.:popcorn:

---

### Post by tomaszg on 2010-09-18
Hello,

We've tried everything:
[http://sysresccd.org/Sysresccd-Networking-EN-Iptables-and-netfilter-load-balancing-using-connmark](http://sysresccd.org/Sysresccd-Networking-EN-Iptables-and-netfilter-load-balancing-using-connmark)
[http://home.regit.org/?page_id=7](http://home.regit.org/?page_id=7)
[http://www.spinics.net/lists/netfilter/msg43602.html](http://www.spinics.net/lists/netfilter/msg43602.html)
and many other solutions, including from LARTC.
I don't know is this issue caused by stock kernel (2.6.32-24-server Ubuntu Server 64) or stock iproute2-ss091226 or something else. Iptables v1.4.4.
Always I stop at this point: I cannot forward ports to machines BEHIND a dual wan router, becouse it doesn't work.
I tried whole configuration described here and seems that everything working, expect FORWARDING.
If I inspect conntrack tables using:
CONNTRACK-VIEWER version 1.3
[http://cv.intellos.net](http://cv.intellos.net)
by Patrick Lagace [email]patou@sympatico.ca[/email]
I can see that connection to specifict port is comming, but nothing happens expect SYN_SENT status.
Can anyone help with this issue?

The other problem was that estabilished connections were being closed after let's say 45 minutes of being open.
I don't know what's gonna happend on this configuration.

This is an example, when I'm trying to reach SSH forwarded to 192.168.0.25 on port 4001:

root@Router:~# ~/conntrack-viewer.pl
Active Connections according to /proc/net/ip_conntrack
Proto   Source Address           Remote Address           Service     State        Mark Masq  Name Resolution
tcp     80.xxx.xxx.xxx           95.xxx.xxx.xxx    55695   22              ESTABLISHED     :256
tcp     80.xxx.xxx.xxx           95.xxx.xxx.xxx    49744   4001            SYN_SENT        :256

---

### Post by tomaszg on 2010-11-18
Just for Your records:
Had to SET GATEWAY to Ubuntu box IP on machine, which want to FORWARD, becouse it tried to use different box as out..  resoulting in connection closed flag.
So if have router LAN IP, let's say 192.168.0.1 use this IP as gateway and DNS on forwarded box.

---

### Post by alienprdkt on 2010-11-18
I have only accomplished this on a Gentoo Platform
No Wan just a LAN router 

[http://www.gentoo.org/doc/en/home-router-howto.xml]("http://www.gentoo.org/doc/en/home-router-howto.xml")

The basis should be the same for Ubuntu (iptables, etc).

and for packet shaping (much easier now I noticed then 4 years ago when I setup mine) you can use

[http://ubuntu-snippets.blogspot.com/2008/07/easy-network-traffic-shaping-on-your.html]("http://ubuntu-snippets.blogspot.com/2008/07/easy-network-traffic-shaping-on-your.html")

Even though its not all for Ubuntu I hope this helps out on building a basic home router with traffic control.

---

### Post by ice4ube on 2011-03-02
Hi jbarbieri,

Is it possible to use the technique you outlined to do loadbalancing across multiple Cellular WAN interfaces (like USB modems)? I would like to essentially build a 3G Router on a ubuntu server.

Thanks.

---

### Post by abdullahfaheem on 2012-03-30
Hi jbarbieri,


what we need to do if we want to setup our eth0 and eth2 with static IPs.

do we still need following commands under rc.local file

----------------------

dhclient -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases -sf /usr/local/scripts/wan1.script eth0

dhclient -pf /var/run/dhclient.eth2.pid -lf /var/lib/dhcp3/dhclient.eth2.leases -sf /usr/local/scripts/wan2.script eth2

----------------------


please explain.

---

