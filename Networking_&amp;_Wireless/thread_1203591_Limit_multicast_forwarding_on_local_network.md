---
title: "Limit multicast forwarding on local network"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by DSmidgy on 2009-07-03
I have a problem limiting IPTV multicast fowrarding to certain IPs.
The setup: #MODEM#<--->#UBUNTU-SERVER#<--->#PC1#
On Ubuntu server:
- the forwarding is set up by [ubuntu-ufw]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") instructions,
- [igmpproxy]("http://sourceforge.net/projects/igmpproxy") is installed.

PC1 can open internet sites and watch IPTV that was forwarded by igmpprogy.
But there is also an wireless access point connected on Ubuntu server. A lot of packets are send to the PCs connected through wireless. That makes wireless (internet) connection very slow.

I'm wondering - is there a way to limit the forwarding of the IPTV igmp packets and streams?

For testing I tried to block the traffic to PC1 (IP=.201, eth1 is connected to local lan) with UFW rules in "/etc/ufw/before.rules":
-A ufw-before-forward -p igmp -o eth1 -d 192.168.0.201 -j DROP
-A ufw-before-forward -o eth1 -s 224.0.0.0/4 -d 192.168.0.201 -j DROP
-A ufw-before-forward -o eth1 -s 192.168.0.101 -d 192.168.0.201 -j DROP
-A ufw-before-forward -o eth1 -d 192.168.0.201 -j DROP
but nothing works.

The last filter only disables internet sharing but not IPTV. How can I write the filter, so that IPTV traffic will only be send to PC1?

Thank you for your help,
Domen

---

### Post by DSmidgy on 2009-08-01
Below are the instructions for enabling multicast forwarding from eth0 (internet) to eth1 (lan).

```
# Internet Connection Sharing
/etc/init.d/ufw enable
if [ ! -f /etc/default/ufw.orig ]; then
  mv /etc/default/ufw /etc/default/ufw.orig
  sed "s/^DEFAULT_FORWARD_POLICY=\"DROP\"$/DEFAULT_FORWARD_POLICY=\"ACCEPT\"/" /etc/default/ufw.orig > /etc/default/ufw
fi
if [ ! -f /etc/ufw/sysctl.conf.orig ]; then
  mv /etc/ufw/sysctl.conf /etc/ufw/sysctl.conf.orig
  sed "s/^#net\/ipv4\/ip_forward=1$/net\/ipv4\/ip_forward=1/" /etc/ufw/sysctl.conf.orig > /etc/ufw/sysctl.conf
fi
if [ ! -f /etc/ufw/before.rules.orig ]; then
  mv /etc/ufw/before.rules /etc/ufw/before.rules.orig
  sed "10s/^$/\n# Internet connection sharing\n*nat\n:POSTROUTING ACCEPT [0:0]\n-A POSTROUTING -o eth0 -s 192.168.0.0\/16 -j MASQUERADE\nCOMMIT\n/" /etc/ufw/before.rules.orig > /etc/ufw/before.rules
fi
/etc/init.d/ufw restart
```

```
# Install igmpproxy
apt-get install gcc make
# Check http://sourceforge.net/projects/igmpproxy/ for latest version
wget http://downloads.sourceforge.net/project/igmpproxy/igmpproxy/0.1_beta4/igmpproxy-0.1_beta4.tar.gz?use_mirror=switch
tar -xzf igmpproxy-0.1_beta4.tar.gz
cd igmpproxy-0.1_beta4
./configure
make
make install
vim /usr/local/etc/igmpproxy.conf # or /etc/igmpproxy.conf
```

Add source IPs under "phyint eth0" using "altnet" command.

```
# Start ...
sudo igmpproxy /usr/local/etc/igmpproxy.conf -d 2>/dev/null &
```

There is no need to configure VLC in any ways to display the streams.

---

