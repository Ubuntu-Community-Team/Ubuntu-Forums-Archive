---
title: "Setting up an internal firewall/router with port forwarding"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by bluedust on 2009-07-11
Hello all; I have tried to set create a firewall/router with the ubuntu community guides but I can not get port fordwarding working.

First let me explain mysetup:

I have a hardware router firewall (FW0) for my internet and I am using an old laptop with two NICS as an internal firewall (FW1). I am using FW1 as a dhcp server I have another machine (called BOX1) behind the firewall. My main desktop (BOX0) is not behind FW1; it is connected to (FW0).

BOX1 and FW1 are running ubunter server 9.

BOX1 can ping the outside world (including BOX0).

My Problem:

I am trying forward traffic on port 8022 on FW1 to port 22 on BOX1. But it is just not working. Here is the script I am using:

```
IPTABLES=/sbin/iptables
AWK=/usr/bin/awk
IFCONFIG=/sbin/ifconfig


# External (Internet-facing) interface
EXTIF="eth0"

# External IP address (automatically detected)
EXTIP="`$IFCONFIG $EXTIF | $AWK /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"

# Internal interface
INTIF="eth1"

# Internal IP address (in CIDR notation)
INTIP="$(ifconfig eth1 | sed -n '2p' | cut -d' ' -f12 | sed 's/^addr://')/32"

# Internal network address (in CIDR notation)
INTNET="$(ifconfig eth1 | sed -n '2p' | cut -d' ' -f12 | sed 's/^addr://'| cut -d'.' -f1-3).0/24"

# The address of anything/everything (in CIDR notation)
UNIVERSE="0.0.0.0/0"


echo "External: [Interface=$EXTIF] [IP=$EXTIP]"
echo "Internal: [Interface=$INTIF] [IP=$INTIP] [Network:$INTNET]"

echo
echo -n "Loading rules..."

# Enabling IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward


# Clear any existing rules and set the default policy to DROP
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -F -t nat

# Delete all User-specified chains
$IPTABLES -X

# Reset all IPTABLES counters
$IPTABLES -Z

###################################################
# INPUT: Incoming traffic from various interfaces #
###################################################

# Loopback interface is valid
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interface, local machines, going anywhere is valid
$IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT


# Remote interface, claiming to be local machines, IP spoofing, get lost
$IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j REJECT


# External interface, from any source, for ICMP traffic is valid
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT


# Allow any related traffic coming back to the MASQ server in.
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT


# Internal interface, DHCP traffic accepted
$IPTABLES -A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
$IPTABLES -A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT


# External interface, HTTP/HTTPS traffic allowed
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 443 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 8022 -j ACCEPT

# External interface, SSH traffic allowed
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 22 -j ACCEPT


# Catch-all rule, reject anything else
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT


####################################################
# OUTPUT: Outgoing traffic from various interfaces #
####################################################

# Workaround bug in netfilter
$IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP

# Loopback interface is valid.
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interfaces, any source going to local net is valid
$IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT


# local interface, MASQ server source going to the local net is valid
$IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT


# outgoing to local net on remote interface, stuffed routing, deny
$IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j REJECT


# anything else outgoing on remote interface is valid
$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT


# Internal interface, DHCP traffic accepted
$IPTABLES -A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT


# Catch all rule, all other outgoing is denied and logged.
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT


###########################
# Packet Forwarding / NAT #
###########################

# ----- Begin OPTIONAL FORWARD Section -----

#Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 1234 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 1234 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.100:1234

#Optionally forward incoming tcp connections on port 8022 to 192.168.2.10
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 8022 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 8022 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.2.10:22


# ----- End OPTIONAL FORWARD Section -----


# Accept solicited tcp packets
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED  -j ACCEPT

# Allow packets across the internal interface
$IPTABLES -A FORWARD -i $INTIF -o $INTIF -j ACCEPT

# Forward packets from the internal network to the Internet
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch-all REJECT rule
$IPTABLES -A FORWARD -j REJECT

# IP-Masquerade
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


echo " done."
```This is bascally a modifed version of the script found here:
[https://help.ubuntu.com/community/Router/Firewall](https://help.ubuntu.com/community/Router/Firewall)

The main things I added were:
```

# ----- Begin OPTIONAL FORWARD Section -----

#Optionally forward incoming tcp connections on port 8022 to 192.168.2.10
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 8022 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 8022 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.2.10:22


# ----- End OPTIONAL FORWARD Section -----

```This was to allow the forwarding; I later added the following line because I though port 8022 was not open:

```
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 8022 -j ACCEPT
```Can anyone help? I would like to know what I am doing wrong and how I can enable logging to see where things stop working.

---

