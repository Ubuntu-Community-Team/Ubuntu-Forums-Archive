---
title: "NAT Setup in Ubuntu Server 10.10"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by darmeg on 2011-03-27
Is it possible to setup NAT in Ubuntu Server 10.10? I have a home network setup, and I want to setup a Domain Controller. The computer I am using has 2 NIC's in it. I have one statically setup with my IP from my ISP, and the other NIC is statically asigned with a private IP. I want to use NAT to assign private IPs to my network. 

I'm sure it's probably possible to setup NAT in linux, but I have no idea what services/roles I would need to setup. I'm not too sure of all the commands and stuff I need to run in linux. In windows it would be simple enough, but I am new to linux.

Hope you can help.

---

### Post by gordintoronto on 2011-03-27
Is there some advantage to turning a computer into a router, instead of spending $30 on a real router?

A domain controller doesn't normally do the things a router does. It's actually DHCP which assigns IP addresses.

---

### Post by Cheesehead on 2011-03-27
Seem like you want a basic router.

Here's how I did it. Your mileage may vary. **Make backups before you start**. You've been warned. 
WARNING: Your Windows skills may lead you astray. For example, the kernel changes do not require a reboot.

1) Edit /etc/network/interfaces to make your LAN connection static instead of dynamic. Your WAN connection, of course, should remain dynamic.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The WAN ethernet jack
auto eth0
     iface eth0 inet dhcp

# The LAN ethernet jack
auto eth1
iface eth1 inet static
     address 192.168.3.1     #Pick your own network, of course
     network 192.168.3.0
     netmask 255.255.255.0

```

2) Next, install the 'dnsmasq' package and configure by editing /etc/dnsmasq.conf to hand out IPs in the appropriate range.

3) Change the kernel settings to permit IP Forwarding. Edit /etc/sysctrl.conf:
```

#   Around line 29
net.ipv4.ip_forward=1                 # Uncomment the line

```

4) Create a set of IPTables rules to permit NAT. Save this script as /etc/network/if-up.d/00-firewall. That way, it will run every time an interface is brought up, superseding any other rules you have laying around.
```

#!/bin/sh
PATH=/usr/sbin:/sbin:/bin:/usr/bin

# Delete all previously existing rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# Allow established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ppp0 -o br0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# ALLOW INCOMING OPEN PORTS TO THE SERVER FROM OUTSIDE HERE
#
# Allow outgoing connections from the LAN side
iptables -A FORWARD -i br0 -o ppp0 -j ACCEPT
#
#

# Masquerade
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Reject any non-established connections from the WAN
iptables -A INPUT -m state --state NEW -i ppp0 -j REJECT
iptables -A FORWARD -i ppp0 -o br0 -j REJECT

```

5) Make it work. It should start automatically upon reboot. But to test it without rebooting (good idea), here's how to make it work:
```

sudo sysctl -p                            # Apply the kernel changes
sudo service dnsmasq restart       # Reload the changed dnsmaq.conf
sudo ifdown eth0
sudo ifdown eth1                        # Reload changed interface and IPTables
sudo ifup eth0
sudo ifup eth1                            # Reload changed interface and IPTables

```

---

### Post by espressobeanie on 2011-04-15
There is if you want to save $30 and have your computer be a server + router and learn Linux more.

---

