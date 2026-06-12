---
title: "Performance Problems with Network Configuration"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by smart-ebusiness on 2010-07-30
Hello,

I be new in that forum and make my first posting. I have configured a server system with 7 servers. one of the server are the router / gateway to the internet. I have big problems with the network performance. E.g. the ssh connection needs 45 to 60sec to establish the connection to another server in the network. I cannot ping from a server in the internal net to the internet.

Here are the configurations

Server 1 (Gateway to Internet)
# The loopback network interface
auto lo
iface lo inet loopback

# The external network interface
auto eth0
iface eth0 inet static
        address xxx.yyy.zzz.xxx
        netmask 255.255.255.224
        network xxx.xxx.xxx.xxx
        broadcast xxx.xxx.xxx.xxx
        gateway xxx.yyy.aaa.bbb
        dns-nameservers xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy
        dns-search domainname.server.com
        post-up iptables-restore < /etc/iptables.up.rules
        # dns-* options are implemented by the resolvconf package, if installed

# The storage + management network interface
auto eth1
iface eth1 inet manual
#        address 10.2.0.1
#        netmask 255.255.255.0
#        network 10.2.0.0
#        broadcast 10.2.0.255
#        gateway xxx.yyy.aaa.bbb

auto br0
iface br0 inet static
        address 10.2.0.1
        netmask 255.255.255.0
        network 10.2.0.0
#        gateway xxx.yyy.aaa.bbb
        bridge_ports eth1
        bridge_fd 0
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

# The campus network interface
auto eth2
iface eth2 inet manual
#        address 10.1.0.1
#        netmask 255.255.255.0
#        network 10.1.0.0
#        broadcast 10.1.0.255
#        gateway xxx.yyy.aaa.bbb

auto br1
iface br1 inet static
        address 10.1.0.1
        netmask 255.255.255.0
        network 10.1.0.0
#        gateway xxx.yyy.aaa.bbb
        bridge_ports eth2
        bridge_fd 0
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

# The heartbeat network interface
auto eth3
iface eth3 inet static
        address 10.10.10.100
        netmask 255.255.255.0
        network 10.10.10.0
        broadcast 10.10.10.255
#        gateway xxx.yyy.aaa.bbb

Server 2
 The loopback network interface
auto lo
iface lo inet loopback

# The campus network interface
auto eth0
iface eth0 inet static
        address 10.1.0.161
        netmask 255.255.255.0
        network 10.1.0.0
        broadcast 10.1.0.255
        gateway 10.1.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.1.0.1 xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy
        dns-search domainname.server.com

# The storage + management network interface
auto eth1
iface eth1 inet static
        address 10.2.0.161
        netmask 255.255.255.0
        network 10.2.0.0
        broadcast 10.2.0.255
        gateway 10.2.0.1

Maybe something ist wrong with the configutation. I am using NAT configured with iptables an sysclt.

I hope I find a very good solution for the problems.

Tahnk you in advance, Ralf

---

