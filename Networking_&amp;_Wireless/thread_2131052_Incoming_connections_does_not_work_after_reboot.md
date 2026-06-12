---
title: "Incoming connections does not work after reboot"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by punik on 2013-03-31
I have a problem, which I can not explain. I am using Ubuntu server 12.04 LTS as a home gateway. Remotely rebooting the system, I noticed that sometimes after reboot I can not access it. SSH, web server, any other software with listening ports is not accessible. that is terribly annoying, because local access is required to reboot the system once more (or several times) until remote access will appear. Strange but from the local network everything works fine (server is running as a gateway), so I need to test accessibility from the internet from my phone after every restart. The firewall is accepts all incoming connections. 

This is my interfaces file. eth0 is looking on ISP network, eth1 - LAN network, eth0.6 - IPTV VLAN

```

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        dns-domain lo
        dns-search lo
        dns-nameservers 127.0.0.1
        post-up iptables-restore < /etc/iptables.up.rules

auto eth0.6
iface eth0.6 inet dhcp
vlan-raw-device eth0

auto eth1
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
dns-nameservers 192.168.0.1

```

Maybe anyone have an idea what i need to do in this complicated situation?

---

### Post by punik on 2013-04-02
Any ideas why this is happening? I did not find anything suspicious in the logs, maybe I do not know what to look for ..

---

