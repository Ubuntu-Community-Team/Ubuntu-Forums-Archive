---
title: "[HOWTO] Setup a Network Gateway"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by sc0g on 2009-09-26
This is a fairly simple tutorial for the average linux user that would like to setup a Network Gateway for their home or business.

**What you need**
- Wireless Router (or a Switch)
- Computer with TWO (2) NICs (Network Interface Cards)

There are three main pieces to my network gateway:
[LIST=1]
[*]Firewall Script
[*]init.d Script
[*]rc.d Symbolic Links
[/LIST]

Here is the firewall script: _/usr/local/sbin/fw_
```

#!/bin/sh
PATH=/usr/sbin:/sbin:/bin:/usr/bin
IPTABLES=/sbin/iptables

# Network Gateway Firewall Script
#
# Configure the variables below accordingly.
# Outside Interface
PUB_IFACE="eth0"
PUB_TCP_PORTS="22 80 443"
PUB_UDP_PORTS=""

# Inside Interface
INT_IFACE="eth1"
INT_TCP_PORTS="21 22 80 443 3128"
INT_UDP_PORTS=""

# Default Policy : ACCEPT DROP or REJECT
POLICY="DROP"

# Networks we're going to MASQ to the Outside Interface
LOCAL_NETWORKS="10.0.1.0/24"

# Network Interfaces
outsideif="$PUB_IFACE"       # aka PUB_IFACE
insideif="$INT_IFACE"        # aka INT_IFACE
loopback="lo"

# Leave this alone unless you want to add your
# inside and outside IP addresses manually
insideip=`/sbin/ifconfig $insideif | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`
outsideip=`/sbin/ifconfig $outsideif | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`
everyone="0.0.0.0/0"
#########################################################

# CUSTOM RULES
# Add your custom networking rules below!
custom_rules() {
# Port Forwarding Example

# This is for a game called Company of Heroes.
# You can delete all of this if you want
#COH_PORTS="6112,9100,45780,1025"
#${IPTABLES} -t nat -A PREROUTING -i $outsideif -p tcp -m multiport --dport $COH_PORTS -j DNAT --to-destination 10.0.1.15
#${IPTABLES} -t nat -A PREROUTING -i $outsideif -p udp -m multiport --dport $COH_PORTS -j DNAT --to-destination 10.0.1.15
#${IPTABLES} -A INPUT -i $outsideif -p tcp -m multiport --dport $COH_PORTS -j ACCEPT
#${IPTABLES} -A INPUT -i $outsideif -p udp -m multiport --dport $COH_PORTS -j ACCEPT
#${IPTABLES} -A FORWARD -i $outsideif -o $insideif -p tcp -m multiport --dport $COH_PORTS -j ACCEPT
#${IPTABLES} -A FORWARD -i $outsideif -o $insideif -p udp -m multiport --dport $COH_PORTS -j ACCEPT

# Allow DHCP broadcasts from the inside
${IPTABLES} -A INPUT -i $insideif -p udp -m multiport --dport 67:68 -j ACCEPT
${IPTABLES} -A INPUT -i $insideif -p tcp -m multiport --dport 67:68 -j ACCEPT

# Ignore NetBIOS because it's annoying!
${IPTABLES} -A INPUT -p tcp -m multiport --dport 137:139 -j REJECT
${IPTABLES} -A INPUT -p udp -m multiport --dport 137:139 -j REJECT

# Ignore SNMP
${IPTABLES} -A INPUT -i $insideif -p tcp --dport 161 -j REJECT
${IPTABLES} -A INPUT -i $insideif -p udp --dport 161 -j REJECT

# Go around SQUID proxy for WeatherDirect
${IPTABLES} -t nat -I PREROUTING -i $insideif -p tcp -s 10.0.1.7 --dport 80 -j ACCEPT
${IPTABLES} -I FORWARD -i $insideif -o $outsideif -p tcp -s 10.0.1.7 --dport 80 -j ACCEPT

# Redirect outbound HTTP requests to the Squid3 web proxy!
${IPTABLES} -t nat -I PREROUTING -i $insideif -p tcp --dport 80 -j REDIRECT --to-port 3128
${IPTABLES} -t nat -I PREROUTING -i $insideif -p tcp --dport 8080 -j REDIRECT --to-port 3128
}
# END CUSTOM RULES

# RULESET FOR MASQ/NAT'D SUBNETS
#
# The following rules should list connections that are
# to be allowed from the inside subnets to the Internet.

masq_rules() {
SUBNET=$1

# Allow everything from the inside out
${IPTABLES} -A INPUT -i $insideif -s $SUBNET -p tcp -j ACCEPT
${IPTABLES} -A INPUT -i $insideif -s $SUBNET -p udp -j ACCEPT
${IPTABLES} -A FORWARD -i $insideif -o $outsideif -s $SUBNET -p tcp -j ACCEPT
${IPTABLES} -A FORWARD -i $insideif -o $outsideif -s $SUBNET -p udp -j ACCEPT
}
# END MASQ RULES

#
# Leave the stuff below alone unless you know what you're doing!
#
start_fw()
{
# CLEAR CURRENT RULESET
clear_rules

# LOAD MODULES
load_modules

# DEFAULT POLICY DROP
${IPTABLES} -P INPUT $DEFAULT_POLICY
${IPTABLES} -P OUTPUT ACCEPT
${IPTABLES} -P FORWARD $DEFAULT_POLICY

# ACCEPT LOOPBACK CONNECTIONS
${IPTABLES} -A INPUT  -i $loopback -j ACCEPT
${IPTABLES} -A OUTPUT -o $loopback -j ACCEPT

# ACCEPT ICMP (PING)
${IPTABLES} -A INPUT  -p icmp -j ACCEPT
${IPTABLES} -A OUTPUT -p icmp -j ACCEPT
${IPTABLES} -A FORWARD -i $insideif -o $outsideif -p icmp -j ACCEPT

# CREATE A LOG CHAIN
${IPTABLES} -N DROP_AND_LOG
${IPTABLES} -A DROP_AND_LOG -j LOG --log-prefix "DROP "
${IPTABLES} -A DROP_AND_LOG -j REJECT

# Enable IP Forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# PUBLIC TCP PORTS
for port in $PUB_TCP_PORTS ; do
${IPTABLES} -A INPUT   -i $outsideif -d $outsideip -p tcp --dport $port -j ACCEPT
done
# PUBLIC UDP PORTS
for port in $PUB_UDP_PORTS ; do
${IPTABLES} -A INPUT   -i $outsideif -d $outsideip -p udp --dport $port -j ACCEPT
done
# INTERNAL TCP PORTS
for port in $INT_TCP_PORTS ; do
${IPTABLES} -A INPUT   -i $insideif -d $insideip -p tcp --dport $port -j ACCEPT
done
# INTERNAL UDP PORTS
for port in $INT_UDP_PORTS ; do
${IPTABLES} -A INPUT   -i $insideif -d $insideip -p udp --dport $port -j ACCEPT
done

# Enable masquerade for all inside networks!
for networkip in $LOCAL_NETWORKS ; do
# NAT should be one way, deny traffic from
# public interfaces that is addressed to masq'ed networks
${IPTABLES} -A INPUT -i $outsideif -d $networkip -j DROP_AND_LOG

# Block spoofed addresses from outside
${IPTABLES} -A INPUT -s $networkip -i $outsideif -j DROP_AND_LOG

# Setup a NAT rule with MASQ
${IPTABLES} -t nat -A POSTROUTING -s $networkip -o $outsideif -j MASQUERADE

# Allow the following rules for each inside subnet
masq_rules $networkip

########################################################
# Some standard security rule-sets

# Deny outside interface claiming to be local machines from spoofing an IP
${IPTABLES} -A INPUT -i $outsideif -s $networkip -d $everyone -j DROP_AND_LOG

# Inside Interface = Outside IP going to Local Nets is OKAY
${IPTABLES} -A OUTPUT -o $insideif -s $outsideip -d $networkip -j ACCEPT

# Inside Interface = Inside IP going to Local Nets is OKAY
${IPTABLES} -A OUTPUT -o $insideif -s $insideip -d $networkip -j ACCEPT

# Outside Interface = Anyone (who isn't already allowed) trying to go to Local nets is BLOCKED
${IPTABLES} -A OUTPUT -o $outsideif -s $everyone -d $networkip -j DROP_AND_LOG
done

# Final rules for INPUT OUTPUT and FORWARD chains

# Allow ESTABLISHED & RELATED connections back in to the MASQ
${IPTABLES} -A INPUT -i $outsideif -s $everyone -d $outsideip -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow connections OUT and only existing/related IN.
${IPTABLES} -A FORWARD -i $outsideif -o $insideif -m state --state ESTABLISHED,RELATED -j ACCEPT
${IPTABLES} -A FORWARD -i $insideif  -o $outsideif -j ACCEPT

# Load the custom rules we have above
custom_rules

########################################################
# INPUT OUTPUT FORWARD : DROP EVERYTHING ELSE

# Catch all rule, all other forwarding is denied and logged.
${IPTABLES} -A INPUT   -s $everyone -d $everyone -j DROP_AND_LOG
${IPTABLES} -A OUTPUT  -s $everyone -d $everyone -j ACCEPT
${IPTABLES} -A FORWARD -s $everyone -d $everyone -j DROP_AND_LOG
}

stop_fw()
{
# CLEAR RULES
clear_rules

# SET DEFAULT POLICY TO ACCEPT
${IPTABLES} -P INPUT ACCEPT
${IPTABLES} -P OUTPUT ACCEPT
${IPTABLES} -P FORWARD ACCEPT
}

restart_fw()
{
stop_fw
start_fw
}

load_modules()
{
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ip_nat_irc
}

clear_rules()
{
# CLEAR EXISTING RULES
${IPTABLES} -F INPUT
${IPTABLES} -F OUTPUT
${IPTABLES} -F FORWARD
${IPTABLES} -F -t nat

if [ "`${IPTABLES} -L -n | grep DROP_AND_LOG`" ]; then
${IPTABLES} -F DROP_AND_LOG
${IPTABLES} -X DROP_AND_LOG
fi

# RESET COUNTERS
${IPTABLES} -Z
}

case "$1" in
'start')
echo -n "* Starting Firewall..."
start_fw
echo "Done"
;;

'stop')
echo -n "* Stopping Firewall..."
stop_fw
echo "Done"
;;

'restart')
echo -n "* Restarting Firewall..."
restart_fw
echo "Done"
;;
esac

```

Here is my init.d script: _/etc/init.d/fw_
```

#!/bin/sh

fw=/usr/local/sbin/fw
LOCKFILE=/var/lock/fw

lockfile_on()
{
  [ ! -d /var/lock ] && mkdir -m 0755 /var/lock
  mkdir -m 0700 $LOCKFILE 2>/dev/null
  if [ $? -ne 0 ]; then
    echo "* ERROR: Firewall currently being reset or lock is stuck."
    echo "         To un-stick, remove the directory $LOCKFILE"
    exit 1
  fi
}

lockfile_off()
{
  rmdir $LOCKFILE 2>/dev/null
}

case "$1" in
  'start')
   lockfile_on
   ${fw} start
   lockfile_off
   ;;
  'stop')
   lockfile_on
   ${fw} stop
   lockfile_off
   ;;
   'restart')
   lockfile_on
   ${fw} restart
   lockfile_off
   ;;
   'help')
   echo "Usage: $0 [start|stop|restart]"
   exit 0
   ;;
esac

```

Here are the commands to create the soft symbolic links:
```

ln -s /etc/init.d/fw /etc/rc0.d/K30fw
ln -s /etc/init.d/fw /etc/rc1.d/K30fw
ln -s /etc/init.d/fw /etc/rc2.d/S30fw
ln -s /etc/init.d/fw /etc/rc3.d/S30fw
ln -s /etc/init.d/fw /etc/rc4.d/S30fw
ln -s /etc/init.d/fw /etc/rc5.d/S30fw
ln -s /etc/init.d/fw /etc/rc6.d/K30fw

```

Also, if you want to run DHCP on your LAN, make sure you disable it on your Router. I am using the **dhcp3-server** package to run DHCP on my network.

Here is how my configuration file looks: _/etc/dhcp3/dhcpd.conf_

```

option domain-name-servers 205.152.37.23, 205.152.132.23;

default-lease-time 84500;
max-lease-time 120000;
log-facility local7;

# Local LAN will use 10.0.1.0/24 Subnet
subnet 10.0.1.0 netmask 255.255.255.0 {
  option routers 10.0.1.10;              # This is the INSIDE IP of my Network Gateway/Linux Server
  range 10.0.1.11 10.0.1.150;
}

# Assign some Static Addresses on my Local Area Network
  host desktop {
  hardware ethernet 00:21:29:65:18:98;
  fixed-address 10.0.1.15;
}

host netbook {
  hardware ethernet 00:24:2b:7c:8d:d2;
  fixed-address 10.0.1.26;
}

```

*I have a more detailed tutorial [posted here]("http://www.scoglan.com/b/?p=16"). When I get some more time, I'll clean up this post once people show some interest in it!*

Feel free to post comments or questions. I'd be glad to help whoever I can. Thanks! :P

---

