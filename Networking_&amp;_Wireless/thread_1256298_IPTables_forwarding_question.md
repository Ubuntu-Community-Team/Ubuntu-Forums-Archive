---
title: "IPTables forwarding question"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by uidzer0 on 2009-09-02
Hey everyone,

I've got a mailserver behind my firewall which forwards all connections to port 25/143 to the internal address 192.168.1.5. External connections work great, however when I attempt to connect to the external IP address on port 25/143 from the internal network, the connection is refused or just hangs. 

Any thoughts?

```

echo "Flushing iptables rules..."
iptables -F 
iptables -t nat -F
iptables -t mangle -F

echo "Enabling kernel forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

echo "Denying SYN floods..."
echo 1 > /proc/sys/net/ipv4/tcp_syncookies

echo "Setting default policies..."
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT


# LAN routing to internet
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

# SMTP traffic
iptables -A FORWARD -p tcp --dport 25 -j ACCEPT

# IMAP traffic
iptables -A FORWARD -p tcp --dport 143 -j ACCEPT

# Established connections
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

echo "Accepting (some) external connections to the router..."
iptables -A INPUT -p tcp --dport 25 -j ACCEPT
iptables -A INPUT -p tcp --dport 143 -j ACCEPT
iptables -A INPUT -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

echo "Accepting local connections to the router..."
iptables -A INPUT -i eth0 -s 0/0 -d 0/0 -j ACCEPT
iptables -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT

echo "Setting up NAT..."
iptables -A POSTROUTING -t nat -o eth1 -j SNAT --to 68.64.214.18

echo "Forwarding mail traffic"
iptables -t nat -A PREROUTING -p tcp --dport 25 -j DNAT --to-destination 192.168.1.5:25
iptables -t nat -A PREROUTING -p tcp --dport 143 -j DNAT --to-destination 192.168.1.5:143

```

---

