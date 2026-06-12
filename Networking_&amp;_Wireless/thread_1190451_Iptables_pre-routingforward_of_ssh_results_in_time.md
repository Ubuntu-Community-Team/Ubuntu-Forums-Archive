---
title: "Iptables pre-routing/forward of ssh results in timed out connection"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by xanas3712 on 2009-06-17
I have several other forward rules to use as examples here and they all work (at least I know I can host warcraft 3 games just fine with the ports) but yet doing the same with ssh doesn't seem to work.

I've tried temporarily using port 22 on external so the port would be the same but that wouldn't work, and looking at examples on the net it appears it should really let me redirect 23 on external to 22 internal. 

I even set ssh temporarily to 23 and tried and it still wouldn't work.

Here's the most immediately relevant portion

```

#Attempting to allow internal SSH access on a specific machine to the outside via port 23.
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 23 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 23 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.101:22
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 23 -j DNAT --to 192.168.0.101:22
#(I've tried 22 & 23 for the forward rule and neither seems to work.... even tried both once)
$IPTABLES -A FORWARD -p tcp -d 192.168.0.101 --dport 23 -o $INTIF -j ACCEPT

```

Here's my firewall script

```

#!/bin/sh

IPTABLES=/sbin/iptables
AWK=/usr/bin/awk
IFCONFIG=/sbin/ifconfig


# External (Internet-facing) interface
EXTIF="eth0"

# External IP address (autmatically detected)
EXTIP="`$IFCONFIG $EXTIF | $AWK /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"
 
# Internal interface
INTIF="eth1"

# Internal IP address (in CIDR notation)
INTIP="192.168.0.1/32"

# Internal network address (in CIDR notation)
INTNET="192.168.0.0/24"

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
#$IPTABLES -P OUTPUT DROP
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

$IPTABLES -A INPUT -i eth0 -s $UNIVERSE -d $UNIVERSE -p tcp --dport 8080 -j ACCEPT
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

# External interface, SSH traffic allowed
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 22 -j ACCEPT

# Catch-all rule, reject anything else
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT


####################################################
# OUTPUT: Outgoing traffic from various interfaces #
####################################################

# Workaround bug in netfilter
#$IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP

# Loopback interface is valid.
#$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interfaces, any source going to local net is valid
#$IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT


# local interface, MASQ server source going to the local net is valid
#$IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT


# outgoing to local net on remote interface, stuffed routing, deny
#$IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j REJECT


# anything else outgoing on remote interface is valid
#$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT


# Internal interface, DHCP traffic accepted
#$IPTABLES -A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT


# Catch all rule, all other outgoing is denied and logged. 
#$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT


###########################
# Packet Forwarding / NAT #
###########################

# ----- Begin OPTIONAL FORWARD Section -----

#Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 1234 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 1234 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.100:1234

#Attempting to allow internal SSH access on a specific machine to the outside via port 23.
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 23 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 23 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.101:22
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 23 -j DNAT --to 192.168.0.101:22
$IPTABLES -A FORWARD -p tcp -d 192.168.0.101 --dport 23 -o $INTIF -j ACCEPT
# ----- End OPTIONAL FORWARD Section -----

#Warcraft 3 forwarding
$IPTABLES -A FORWARD -p tcp -d 192.168.0.101 --dport 6112 -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -p udp -d 192.168.0.101 --dport 6112 -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -p tcp -d 192.168.0.102 --dport 6114 -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -p udp -d 192.168.0.102 --dport 6114 -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -p tcp -d 192.168.0.106 --dport 6116 -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -p udp -d 192.168.0.106 --dport 6116 -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -p tcp -d 192.168.0.150 --dport 6118 -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -p udp -d 192.168.0.150 --dport 6118 -o $INTIF -j ACCEPT

$IPTABLES -A FORWARD -p tcp -d 192.168.0.101 --dport 4662 -o $INTIF -j ACCEPT

# Accept solicited tcp packets
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED  -j ACCEPT

# Allow packets across the internal interface
$IPTABLES -A FORWARD -i $INTIF -o $INTIF -j ACCEPT

# Forward packets from the internal network to the Internet
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch-all REJECT rule
$IPTABLES -A FORWARD -j REJECT

# IP-Masquerade
#$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

#Warcraft 3 nat rules
$IPTABLES -t nat -A PREROUTING -t nat -p tcp -d $EXTIP --dport 6112 -j DNAT --to 192.168.0.101:6112
$IPTABLES -t nat -A PREROUTING -t nat -p udp -d $EXTIP --dport 6112 -j DNAT --to 192.168.0.101:6112
$IPTABLES -t nat -A PREROUTING -t nat -p tcp -d $EXTIP --dport 6114 -j DNAT --to 192.168.0.102:6114
$IPTABLES -t nat -A PREROUTING -t nat -p udp -d $EXTIP --dport 6114 -j DNAT --to 192.168.0.102:6114
$IPTABLES -t nat -A PREROUTING -t nat -p tcp -d $EXTIP --dport 6116 -j DNAT --to 192.168.0.106:6116
$IPTABLES -t nat -A PREROUTING -t nat -p udp -d $EXTIP --dport 6116 -j DNAT --to 192.168.0.106:6116
$IPTABLES -t nat -A PREROUTING -t nat -p tcp -d $EXTIP --dport 6118 -j DNAT --to 192.168.0.150:6118
$IPTABLES -t nat -A PREROUTING -t nat -p udp -d $EXTIP --dport 6118 -j DNAT --to 192.168.0.150:6118

$IPTABLES -t nat -A PREROUTING -t nat -p tcp -d $EXTIP --dport 4662 -j DNAT --to 192.168.0.101:4662
echo " done."

```

---

### Post by gombadi on 2009-06-17
Is this a typo or the problem?


> 
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 23 -j DNAT --to 192.168.0.101:22
$IPTABLES -A FORWARD -p tcp -d 192.168.0.101 --dport 23 -o $INTIF -j ACCEPT


In the prerouting table you NAT the connection to port 22. When the packet gets to the FORWARD table you allow packets to destination port 23 so the packet you NATTED to port 22 will not match.

Sometimes, on a temporary basis, it pays to add a rule to LOG dropped packets so you can see what the firewall is dropping.

---

### Post by xanas3712 on 2009-06-17
Unfortunately not, you probably read this before I made the edit.

#(I've tried 22 & 23 for the forward rule and neither seems to work.... even tried both once)

I'm also not sure exactly how to log packet drops but I'll look into that.

Also, I tried flushing and using P Accept with everything except the nat rules in order to rule out any of that forwarding stuff.

I even tried using rinetd to forward the port since that was discussed elsewhere (I did make sure the port 23 was open on server at the time so that rinetd could try to do it's thing).

The iptables -L -vnx does reflect that some packets are going through that rule..

> 
   2      120 ACCEPT     tcp  --  *      eth1    0.0.0.0/0            192.168.0.101       tcp dpt:22


Checking iptables -L -t nat -vnx gets..

> 
 1       60 DNAT       tcp  --  *      *       0.0.0.0/0            72.48.215.233       tcp dpt:23 to:192.168.0.101:22


So it looks like stuff is getting through.. but.. notbeing accepted for some reason.

Is there something in the default sshd config that might be rejecting this?  

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2

HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by gombadi on 2009-06-18
> 
I'm also not sure exactly how to log packet drops but I'll look into that.


Add the following to the end of the script you have. You can also add the same line for the output and forward tables. It will add a rule to log any packets just before the default policy drops them. As you are also getting some hits on the rules you can use tcpdump to have a look at the packets to see if you can find out where they are going.

```

iptables -A INPUT -p tcp -d 192.168.0.101 -m limit --limit 5/min -j LOG --log-prefix "some text here"

```

---

