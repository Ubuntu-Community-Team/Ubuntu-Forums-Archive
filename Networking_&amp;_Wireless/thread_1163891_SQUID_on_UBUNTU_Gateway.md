---
title: "SQUID on UBUNTU Gateway"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by akkumaru on 2009-05-19
hello,,

i'm trying to set up an ubuntu gateway with SQUID transparent proxy.

after some quite exhausting days, this is what i have so far:

```
## FWD TO SQUID ##
iptables -t nat -A PREROUTING -s $INTERNET_IP -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -i $INTERNET_IFACE -p tcp --dport 80 -j DNAT --to-destination $INTERNAL_IP:$SQUID_PORT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

## ICS ##
iptables -A FORWARD -i $INTERNET_IFACE -o $INTERNAL_IFACE -s $INTERNAL_NETWORK -m state --state NEW -j FIREWALL
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j FIREWALL
iptables -t nat -A POSTROUTING -j MASQUERADE
```

$INTERNET_IP is the IP Address for the $INTERNET_IFACE
while $INTERNAL_IP for $INTERNAL_IFACE

with /etc/squid/squid.conf

> http_port 192.168.0.1:8888 transparent

# log & error
access_log /var/log/squid/access.log squid
error_directory /usr/share/squid/errors

..acl..

then, on terminal:

```
sudo squid -z
sudo squid -k reconfigure
```

i don't think this is quite right at the moment (my clients can't get access to the internet on port 80), so please, can anyone tell me some example configuration that really works,,?

on iptables, where should i direct the packet coming from port 80?
and on squid.conf, where should i set the squid listen to?
to the $INTERNAL_IFACE or $INTERNET_IFACE,,?

as for note, i also add the [fordon's firewall script]("http://ubuntuforums.org/showthread.php?t=668148") to the iptables script.

thank you,

---

### Post by akkumaru on 2009-05-21
i see,,
so in the first place, i need to handle FORWARD chain separately,,

actually, it's been two weeks, since i tried to compose your firewall script with squid as transparent proxy in an ubuntu gateway,,

whenever i try to fuse the two,
i notice that the firewall drop some packets so that the web traffic to the clients are interupted,,

if i disable the firewall, the squid runs alright,
if i disable the squid, the firewall doesn't give any problem,

well, the fast question is, how should i open the squid for your firewall?

also, is this right: "if i use squid as transparent proxy in a gateway, then there will be no FORWARD chain for web traffic, as the FORWARD packet from LAN would become INPUT for squid and squid will then forward the packet as OUTPUT" ?

thank you,

this is what i have so far:
```

#! /bin/sh

# SET VARIABLES
INTERNET_IP="192.168.1.2"
INTERNAL_IP="192.168.0.1"
INTERNAL_NETWORK="192.168.0.0/24"

INTERNET_IFACE="eth1"
INTERNAL_IFACE="eth0"

SQUID_PORT="8888"

# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X

####################################--FIREWALL--####################################
# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED

# Log Chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
###############################
#iptables -A LOG_DROP -j DROP #  FINAL DROP HERE !!!
###############################

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i $INTERNAL_IFACE -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT

# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED

# DROP all other packets
iptables -A FIREWALL -j LOG_DROP

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A OUTPUT -j FIREWALL

# ** ALLOWED LIST ** #
#--------------------#
# Allow dns
iptables -A TRUSTED -o $INTERNET_IFACE -p udp -m udp --dport 53 -j ACCEPT
#iptables -A TRUSTED -i $INTERNET_IFACE -p udp -m udp --sport 53 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 53 -j ACCEPT
#iptables -A TRUSTED -i $INTERNET_IFACE -p tcp -m tcp --sport 53 -j ACCEPT

# Allow http
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i $INTERNET_IFACE -p tcp -m tcp --sport 80 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow https
iptables -A TRUSTED -o $INTERNET_IFACE -p udp -m udp --dport 443 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 443 -j ACCEPT

#Allow IRC IDENT & DCC
#iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 6667 -j ACCEPT
#iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state NEW -j ACCEPT

# Allow pop3s (SSL)
iptables -A TRUSTED -o $INTERNET_IFACE -p udp -m udp --dport 995 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 995 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p udp -m udp --dport 110 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 110 -j ACCEPT

# Allow smtp
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 25 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 465 -j ACCEPT

# Allow imap2
iptables -A TRUSTED -o $INTERNET_IFACE -p udp -m udp --dport 143 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 143 -j ACCEPT

# Allow imap3
iptables -A TRUSTED -o $INTERNET_IFACE -p udp -m udp --dport 220 -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 220 -j ACCEPT

# Allow newsgroup
#iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 119 -j ACCEPT

# Allow ftp
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow YAHOO!MESSENGER
iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 5050 -j ACCEPT
iptables -A TRUSTED -i $INTERNET_IFACE -p tcp -m tcp --dport 5050 -j ACCEPT

# SQUID
# allow INPUT FROM LAN to SQUID
iptables -A TRUSTED -i $INTERNAL_IFACE -p tcp -m tcp --dport $SQUID_PORT -j ACCEPT
# allow OUTPUT from SQUID, basically allowing http traffic
# iptables -A TRUSTED -o $INTERNET_IFACE -p tcp -m tcp --dport 80 -j ACCEPT
# allow OUTPUT FROM SQUID TO LAN
iptables -A TRUSTED -o $INTERNAL_IFACE -p tcp -m tcp --sport $SQUID_PORT -j ACCEPT

# WEBMIN
iptables -A TRUSTED -o $INTERNAL_IFACE -p tcp -m tcp --dport 10000 -j ACCEPT
iptables -A TRUSTED -i $INTERNAL_IFACE -p tcp -m tcp --dport 10000 -j ACCEPT

####################################--FIREWALL--####################################

# FWD ALL ACCESS TO SQUID #
#iptables -t nat -A PREROUTING -i $INTERNET_IFACE -p tcp --dport 80 -j DNAT --to-destination $INTERNAL_IP:$SQUID_PORT
iptables -t nat -A PREROUTING -i $INTERNAL_IFACE -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

## ICS FOR OTHER THAN WEB TRAFFIC ##
iptables -A FORWARD -i $INTERNET_IFACE -o $INTERNAL_IFACE -s $INTERNAL_NETWORK -m state --state NEW -j FIREWALL
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING -j MASQUERADE

# End message
echo "\n..running....."

```

---

### Post by frodon on 2009-05-22
First at the end of your FORWARD chain rules you should have :
```
iptables -A FORWARD -j DROP
```Thus you are sue to drop the packets you don't have explicitely allowed.

For the rest the following tutorial should answer many of your questions:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

---

### Post by bapoumba on 2009-05-22
Two posts merged in here.

---

### Post by ibuclaw on 2009-05-22
May I also add that once you have your firewall setup, you can run:
```
sudo iptables-save | sudo tee /etc/iptables.rules
```

and then restore the configuration at boot by putting:
```
/sbin/iptables-restore < /etc/iptables.rules
```
in the **/etc/rc.local** file.

But, of course, if you don't expect your firewall to remain static, the way you are doing it now is just as fine, if not a little bit slower. ;)

Regards
Iain

---

### Post by &#27969;&#27801;&#26539; on 2009-05-22
&#65293;_&#65293;&#65281;&#65281;
[IMG]http://ubuntuforums.org/images/misc/ubuntulogo.png[/IMG]

---

### Post by akkumaru on 2009-05-24
yes, i've made the iptables configuration permanent,
i wrote the script in a file, then made it executable,
i called the script from /etc/rc.local, so it would be running every time the computer boots


i've read the link frodon gave,
i suppose it is quite correct that:
"if the gateway is also a squid transparent proxy server, there will be NO FORWARD chain for http traffic (or for whatever forwarded to the squid server)"

---

### Post by akkumaru on 2009-05-26
here is some principles to build firewall-squid_proxy as http transparent proxy:

```

# redirect web traffic from LAN to SQUID
iptables -t nat -A PREROUTING -i $LAN -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

# from LAN to SQUID
# allow INPUT from LAN_IFACE (port ANY) to SQUID for NEW state
iptables -A INPUT -j ACCEPT -m state	--state NEW,ESTABLISHED,RELATED -i $LAN -p tcp --dport $SQUID_PORT

# from BOX (SQUID) to INET
# allow OUTPUT from INET_IFACE (port ANY) to ANY (port 80) for NEW,ESTABLISHED,RELATED state
iptables -A OUTPUT -j ACCEPT -m state	--state NEW,ESTABLISHED,RELATED -o $INET -p tcp --dport 80

# from INET TO BOX
# allow INPUT from INET_IFACE (port 80) to ANY for ESTABLISHED & RELATED states
iptables -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED -i $INET -p tcp --sport 80

# from BOX (SQUID) to LAN
# allow OUTPUT from LAN_IFACE (port 80) to ANY (port 80) for ESTABLISHED,RELATED state
iptables -A OUTPUT -j ACCEPT -m state --state ESTABLISHED,RELATED -o $LAN -p tcp --sport 80

```

logically:

## ICS without proxy
LAN--->(as FORWARD) GATEWAY (as FORWARD)--->INET : state NEW
LAN<---(as FORWARD) GATEWAY (as FORWARD)<---INET : state ESTABLISHED, RELATED

## ICS with proxy
LAN--->(as INPUT)>>SQUID_PROXY (as OUTPUT)--->INET : state NEW,ESTABLISHED,RELATED
LAN<---(as OUTPUT)<<SQUID_PROXY (as INPUT)<---INET : state ESTABLISHED,RELATED

i'll upload the complete script as soon as i build the firewall for FORWARD chain,,

---

