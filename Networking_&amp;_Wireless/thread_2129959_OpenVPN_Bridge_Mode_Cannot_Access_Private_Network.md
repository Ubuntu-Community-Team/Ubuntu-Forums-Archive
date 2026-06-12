---
title: "OpenVPN Bridge Mode Cannot Access Private Network"
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by deadfish00 on 2013-03-27
I have similar issues found in this forum and I've tried everything indicated there with no result. I've been struggling creating the openVPN in bridge mode and today it finally connected but I couldn't ping my local network (work) from the client machine.

I'm using Ubuntu Server 12.04 for my server and Windows 8 as client (test) 

Here's my config for the OpenVPN
```
port 1194proto udp
dev tap0
ca /etc/openvpn/ca.crt
cert /etc/openvpn/vpn2.crt
key /etc/openvpn/vpn2.key  # This file should be kept secret
dh /etc/openvpn/dh2048.pem

ifconfig-pool-persist ipp.txt
server-bridge 192.168.2.190 255.255.255.0 192.168.2.191 192.168.2.195

push "route 192.168.2.0 255.255.255.0"
push "dhcp-option DNS 192.168.2.19"
push "dhcp-option DOMAIN company.local"
;push "dhcp-option WINS 10.8.0.1"

keepalive 10 120
cipher BF-CBC        # Blowfish (default)


comp-lzo
max-clients 5
persist-key
persist-tun
status openvpn-status.log
verb 3
```

According to the manual from OpenVPN, I have to create and run the script Bridge-Start in order to create br0 and tun0. However because of my eth0 config, it destroy's my link to the gateway. Even when I manually run route command to add a default gateway, I couldn't connect from my Client if I follow the OpenVPN instructions. Here's the link from the OpenVPN Manual: [http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html) 

Here's my config:
```
auto loiface lo inet loopback


auto eth0
iface eth0 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down


auto br0
iface br0 inet static
    #ip, netmask, ecc are the original ones
    address 192.168.2.190
    netmask 255.255.255.0
    gateway    192.168.2.251
    #network interfaces on which to enable the bridge
    bridge_ports eth0
```

If I manually configured the bridge mode in the /etc/network/interfaces, I can use my client to connect to the server just fine. However, when pining the vpn server or any private address, I couldn't ping anything and vice versa. 

I've also modified the sysctl.conf file here: 

```
net.ipv4.ip_forward=1
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0

```

route result
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.251   0.0.0.0         UG    100    0        0 br0
192.168.2.0     *               255.255.255.0   U     0      0        0 br0

```

Please let me know if I missed anything for troubleshooting this issue. As mentioned before, I performed the iptable command from the thread link above and it still didn't work for me. Any help is greatly appreciated

---

### Post by ahallubuntu on 2013-03-27
~

---

### Post by deadfish00 on 2013-03-28
Thanks for the reply! :) 

my gateway for this server is 
```
 192.168.2.251 
```

But  I still need to access the whole 192.168.2.0/24 subnet. I updated the  server-bridge from 192.168.2.190 to 192.168.2.251. Then tried to connect  to it again. I was able to connect to the OpenVPN server but I still  cannot ping any other services in the LAN.

I haven't tried  creating the bridge the way you do because, I need to specify the  gateway to 192.168.2.251. In your config, you've assigned the br0 to  dhcp. How do you connect and know the IP when you use your script to  turn the bridge on? 

Speaking of network configuration, is there anything wrong specifying the eth0 and br0 in the /etc/network/interface file?

---

### Post by deadfish00 on 2013-03-28
Also followed this instructions from OpenVPN to allow tun connections. Here's the link: [http://openvpn.net/index.php/open-source/faq/79-client/255-qconnection-initiated-with-xxxxq-but-i-cannot-ping-the-server-through-the-vpn.html](http://openvpn.net/index.php/open-source/faq/79-client/255-qconnection-initiated-with-xxxxq-but-i-cannot-ping-the-server-through-the-vpn.html) 

I think I've exhausted my options here. Is there a way to know if the iptables rules properly inserted and tested? I have two days left to make this thing work lol

---

### Post by ahallubuntu on 2013-03-28
~

---

### Post by deadfish00 on 2013-03-28
It's still not working for me. I've reconfigured the way you did it and it still not working for me. I pushed the route 192.168.2.0 255.255.255.0 to the client and ensure the ipv4.forwarding is enabled 

```
cat /proc/sys/net/ipv4/ip_forward
```

and it returned 1

---

### Post by ahallubuntu on 2013-03-28
~

---

### Post by deadfish00 on 2013-03-29
I was able to fix it with your config. The problem, imo, was the up.sh config wasn't working correctly. I've configured a VM instead because the fact that it's easier to revert if I made a mistake. Here's my final configuration just in case someone stumbled with the same issue as I am. 

First here's my configuration for my network interface; I only have 1 ethernet in this box
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet manual
        up ip link set $IFACE up promisc on

auto br0
iface br0 inet static
        address 192.168.2.180
        netmask 255.255.255.0
        broadcast 192.168.2.255
        gateway 192.168.2.251
        bridge_ports eth0

        #VMware config
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
        bridge_maxwait 5

```

Additional configuration for ESXi server, I have to _enable promiscuous mode _in the vswitch for the Ethernet to make it work. 

Same script used for the up.sh and down.sh though I've modified my up.sh since I've had issues when running it. 
```

#!/bin/sh


BR=$1
DEV=$2
MTU=$3
/sbin/ifconfig $DEV mtu $MTU promisc up
/sbin/brctl addif $BR $DEV

```

As for the server config I've added the following
```

up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

script-security 3

```

I've had issues when I added 1500 nor eth0 at the end of the up script. Also, I have to add the script-security to run external script (up.sh and down.sh). Also configured the /etc/sysctl.conf to enable ipv4 forwarding. 

Thanks for the assistance [COLOR=#000000]ahallubuntu! :)[/COLOR]

---

### Post by snipehunter on 2013-03-29
I have just been trying to get OpenVPN up and running. I am a complete novice to VPN, but I noticed that my logfiles were being filled with blocked outbound traffic. The OpenVPN forum doesn't mention this, but I figured I needed to give my TUN interface access out so I ran an extra iptables command. After that my connection could ping and would allow internet traffic. Here's the additional command I ran.
```
sudo iptables -A OUTPUT -o tun+ -j ACCEPT
```

---

### Post by deadfish00 on 2013-04-01
Can you share which log files where you found the the outbound traffic being blocked?

---

### Post by snipehunter on 2013-04-04
They were in messages and syslog, and maybe a few others. If they are not showing up there, you may have logging turned off on the firewall, or this may not be your issue.

---

