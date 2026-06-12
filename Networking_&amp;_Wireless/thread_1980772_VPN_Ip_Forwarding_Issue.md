---
title: "VPN Ip Forwarding Issue"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by paulg1981 on 2012-05-15
Hello,

I have two servers one running Ubuntu 10.04.4 LTS and the other running 12.04 LTS. The 10.04 server has been running openvpn flawlessly for months. I copied the config files and certs from the older (10.4) server to the newer (12.04) as I am intending to migrate. I had no issues getting it up and running but the problem is that the new server is not routing to the internet. 

I have the same iptables rules for both servers, using ufw. They are as follows and are located in /etc/ufw/before.rules:

```
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

#Allow forward traffic from tuno to eth0
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j SNAT --to myserverip.1
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j SNAT --to myserverip.2

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines

# allow all traffic via our OpenVPN interface
-A INPUT -i tun0 -j ACCEPT
-A FORWARD -i tun0 -j ACCEPT

# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT

# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```

The rules are standard except for the postrouting rules and the tun0 accept traffic rules.


I have also enabled IP Forwarding in both sysctl.conf and /etc/ufw/sysctl.conf
```
cat /proc/sys/net/ipv4/ip_forward
```
produces "1"

I have also changed the value of /etc/default/ufw so that: 
```
DEFAULT_FORWARD_POLICY="ACCEPT"
```

It is my understanding that this should enable IP Forwarding for ufw firewall. I have also disabled and flush ufw and manually entered the postrouting rules with no success.

My server.conf file is as follows:
```
server 10.8.0.0 255.255.255.0
local  myserverip.1
dev tun
proto udp
comp-lzo
tun-mtu 1500
push "redirect-gateway def1"
push "dhcp-option DNS 208.67.222.222"
keepalive 10 60
dh dh1024.pem
ca ca.crt
cert server.crt
key server.key
user openvpn
group openvpn
persist-key
persist-tun
mute-replay-warnings
status openvpn-status.log
client-to-client
```

and the client profile is:
```
client
dev tun
proto udp
remote myserverip.1 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert DesktopHome.crt
key DesktopHome.key
ns-cert-type server
comp-lzo
verb 3
float
```

I have done tcpdumps for eth0 (internet facing adapter) and tun0 which show the packets passing as expected with the correct source addresses.

I am stumped and I would really appreciate some assistance, I have been working on this issue for 4-5 days now!

---

### Post by paulg1981 on 2012-05-17
Nobody has any ideas?  :-(

---

### Post by bdwernychuk on 2012-05-30
I've got the same problem: migrated my before.rules file from a 10.x LTS firewall that's been running flawlessly for ages to a new 12.04 install and forwarding (of any kind, not just my VPN) does not work. I've been flogging this for about a week and am no farther ahead. The lack of replies is disheartening!

---

