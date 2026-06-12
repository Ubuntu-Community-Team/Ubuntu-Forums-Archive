---
title: "Firewall not forwarding ports anymore."
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by mxa055 on 2006-04-12
Hi there,

until yesterday I had a linux router/firewall PC running just fine. Emule, Torrent, etc where running just fine on a host PC running Windows. Today that I checked my downloads I found out that I had a lowid. After a few minutes of checking things around, I found out that the ports are not forwarded anymore.

The modem I use is a speedtouch 530i with NAPT set to use server 10.0.0.2 (the linux ethernet address that is connected to the modem and thus the outside world.)

The firewall rules I am using on the linux machine are: (this is going to be quite long so bare with me)

```

FWVER=0.88s

echo -e "\nLoading rc.firewall-iptables-STRONGER - version $FWVER..\n"

IPTABLES=/sbin/iptables
LSMOD=/sbin/lsmod
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe
GREP=/bin/grep
AWK=/usr/bin/awk
IFCONFIG=/sbin/ifconfig

EXTIF="eth0"
INTIF="eth1"
LANHOST="192.168.0.2"
echo "  External Interface:  $EXTIF"
echo "  Internal Interface:  $INTIF"
echo "  ---"

EXTIP="`$IFCONFIG $EXTIF | $AWK \
 /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"

echo "  External IP: $EXTIP"
echo "  ---"

INTNET="192.168.0.0/24"
INTIP="192.168.0.1/32"
echo "  Internal Network: $INTNET"
echo "  Internal IP:      $INTIP"
echo "  ---"

UNIVERSE="0.0.0.0/0"

echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a

echo -en "    Loading kernel modules: "

if [ -z "` $LSMOD | $GREP ip_tables | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_tables
fi

echo -en "ip_conntrack, "
if [ -z "` $LSMOD | $GREP ip_conntrack | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_conntrack
fi
echo -e "ip_conntrack_ftp, "
if [ -z "` $LSMOD | $GREP ip_conntrack_ftp | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_conntrack_ftp
fi

echo -en "iptable_nat, "
if [ -z "` $LSMOD | $GREP iptable_nat | $AWK {'print $1'} `" ]; then
   $MODPROBE iptable_nat
fi

echo -e "ip_nat_ftp"

if [ -z "` $LSMOD | $GREP ip_nat_ftp | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_nat_ftp
fi

echo "  ---"
echo "  Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "  Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

echo "  ---"

echo "  Clearing any existing rules and setting default policy to DROP.."
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -F -t nat

$IPTABLES -X
$IPTABLES -Z

echo "  Creating a DROP chain.."
$IPTABLES -N reject-and-log-it
$IPTABLES -A reject-and-log-it -j LOG --log-level info 
$IPTABLES -A reject-and-log-it -j REJECT

echo -e "\n   - Loading INPUT rulesets"

$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
$IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j reject-and-log-it
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state \
 ESTABLISHED,RELATED -j ACCEPT

# eMule/eDonkey
$IPTABLES -A INPUT -i $EXTIF -p tcp -d $EXTIP --sport 1024:65535 --dport 4662 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p udp -d $EXTIP --sport 1024:65535 --dport 4672 -j ACCEPT

# uTorrent
$IPTABLES -A INPUT -i $EXTIF -p tcp -d $EXTIP --sport 1024:65535 --dport 32459 -j ACCEPT

# VNC
$IPTABLES -A INPUT -i $EXTIF -p tcp -d $EXTIP --sport 1024:65535 --dport 5982 -j ACCEPT

$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it

echo -e "   - Loading OUTPUT rulesets"
$IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT
$IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j reject-and-log-it
$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it

# Allow eMule/eDonkey port to get to LANHOST
$IPTABLES -A FORWARD -p tcp -i $EXTIF -o $INTIF -d $LANHOST --sport 1024:65535 --dport 4662 -j ACCEPT
$IPTABLES -A FORWARD -p udp -i $EXTIF -o $INTIF -d $LANHOST --sport 1024:65535 --dport 4672 -j ACCEPT

# uTorrent
$IPTABLES -A FORWARD -p tcp -i $EXTIF -o $INTIF -d $LANHOST --sport 1024:65535 --dport 32459 -j ACCEPT

# VNC
$IPTABLES -A FORWARD -p tcp -i $EXTIF -o $INTIF -d $LANHOST --sport 1024:65535 --dport 5982 -j ACCEPT

echo "     - FWD: Allow all connections OUT and only existing/related IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

$IPTABLES -A FORWARD -j reject-and-log-it

echo "     - NAT: Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP

# Allow eMule/eDonkey
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp -d $EXTIP --sport 1024:65535 --dport 4662 -j DNAT --to $LANHOST:4662
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p udp -d $EXTIP --sport 1024:65535 --dport 4672 -j DNAT --to $LANHOST:4672

#uTorrent
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp -d $EXTIP --sport 1024:65535 --dport 32459 -j DNAT --to $LANHOST:32459

#VNC
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp -d $EXTIP --sport 1024:65535 --dport 5982 -j DNAT --to $LANHOST:5982

#######################################################################
echo -e "\nrc.firewall-iptables-stronger $FWVER done.\n"

```

*I haven't included comments for length reasons. You can find the actual contents of the file with all the comments in the attached .txt file

The ports I need access from the outside are 4662,4672(emule) - 5982 (VNC) -32459(uTorrent)

Until yesterday everything worked fine. Can't remember of changing anything except from a normal restart.

btw the output of iptables -L after running the above script is:

```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  192.168.0.0/24       anywhere
reject-and-log-it  all  --  192.168.0.0/24       anywhere
ACCEPT     icmp --  anywhere             10.0.0.2
ACCEPT     all  --  anywhere             10.0.0.2            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             10.0.0.2            tcp spts:1024:65535 dpt:4662
ACCEPT     udp  --  anywhere             10.0.0.2            udp spts:1024:65535 dpt:4672
ACCEPT     tcp  --  anywhere             10.0.0.2            tcp spts:1024:65535 dpt:32459
ACCEPT     tcp  --  anywhere             10.0.0.2            tcp spts:1024:65535 dpt:5982
reject-and-log-it  all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             loukoumaki          tcp spts:1024:65535 dpt:4662
ACCEPT     udp  --  anywhere             loukoumaki          udp spts:1024:65535 dpt:4672
ACCEPT     tcp  --  anywhere             loukoumaki          tcp spts:1024:65535 dpt:32459
ACCEPT     tcp  --  anywhere             loukoumaki          tcp spts:1024:65535 dpt:5982
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
reject-and-log-it  all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
DROP       icmp --  anywhere             anywhere            state INVALID
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  10.0.0.2             192.168.0.0/24
ACCEPT     all  --  teiresias            192.168.0.0/24
reject-and-log-it  all  --  anywhere             192.168.0.0/24
ACCEPT     all  --  10.0.0.2             anywhere
reject-and-log-it  all  --  anywhere             anywhere

Chain reject-and-log-it (5 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level info
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable
LOG        all  --  anywhere             anywhere            LOG level info
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

```
*Teiresias is the router's hostname, and loukoumaki is 192.168.0.2 (the host where torrent,emule etc are running)

And finally, I get these messages logged into /var/log/messages when trying to test port 32459 from the outside
```

Apr 12 16:46:34 localhost kernel: [4299581.958000] IN=eth0 OUT= MAC=00:d0:70:00:fd:fb:00:0e:50:07:34:44:08:00 SRC=65.94.58.87 DST=10.0.0.2 LEN=125 TOS=0x00 PREC=0x00 TTL=117 ID=3044 PROTO=UDP SPT=32459 DPT=62260 LEN=105
Apr 12 16:46:37 localhost kernel: [4299584.141000] IN=eth0 OUT= MAC=00:d0:70:00:fd:fb:00:0e:50:07:34:44:08:00 SRC=86.126.76.218 DST=10.0.0.2 LEN=125 TOS=0x00 PREC=0x00 TTL=117 ID=33808 PROTO=UDP SPT=32459 DPT=62260 LEN=105

```

Thanks in advance, and sorry for the length!

---

### Post by frodon on 2006-04-13
amule is often a problem with iptables rules because according to the amule.org site ([http://www.amule.org/wiki/index.php/Firewall](http://www.amule.org/wiki/index.php/Firewall)) you must allow outgoing traffic to get HighID, and it's not the case in your configuration.
In addition you forgot to allow and forward the port 4665 in udp for amule, all is explained in the link i gave you.

---

### Post by mxa055 on 2006-04-13
I added udp port 4665 to the firewall script. I haven't tested it yet, but as soon as I do I will let you know.

I doubt that's the end of my problems though, as amule is not the only program that its ports are not forwarded (and it was working in highid earlier without port 4665 being forwarded). Any idea what could be affecting port forwarding in general, given that is was working one day and the next it stopped?

---

