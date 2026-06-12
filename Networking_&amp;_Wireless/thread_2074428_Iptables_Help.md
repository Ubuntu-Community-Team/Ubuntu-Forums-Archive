---
title: "Iptables Help"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by krisdotca on 2012-10-21
I'm trying to set up iptables to block all traffic except ssh but, no matter what I do, it's blocking outgoing ssh. The commands that I'm using are shown below. Oddly, I can SSH into the box, just not out. I'm using Ubuntu Server 10.10 if it makes any difference.

# Flush existing rules
sudo iptables --flush

# default policies
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

# allow unlimited traffic on loopback
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A OUTPUT -o lo -j ACCEPT

# allow ssh
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

---

### Post by The Cog on 2012-10-21
I see nothing there blocking outgoing SSH. Are you sure the problem is not that you are blocking incoming DNS name lookup replies?

---

