---
title: "vpnc traffic routing - IPSec target network"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by dude08 on 2010-11-16
I just got vpnc setup to work with my VPN at work and now I am trying to figure out how to limit the traffic that is routed through the VPN while I'm connected to it. I only want traffic going to the local domain to be routed through the VPN.

This is what my vpnc config file looks like:
```

IPSec gateway publicdomain.example.com
IPSec ID XXXX
IPSec secret YYYY
Xauth username ZZZZZ
Xauth password *****

```Once I connect, vpnc will change my normal ISP nameservers in /etc/resolv.conf to the nameservers on the VPN so I can then resolve IPs on the private local domain to privatedomain.example.com.

Is there a way to make it so that the VPN nameservers are only used for the private local domain and traffic only goes through to the VPN for VPN traffic, and not everything else like normal Internet web browsing using the IPSec target network config option or some other way?

---

### Post by dude08 on 2010-11-17
bump

---

### Post by dude08 on 2010-11-17
I found this great [howto]("http://www.gentoo.org/doc/en/vpnc-howto.xml") on doing this exact task.

Since the above howto is for Gentoo and not Ubuntu, the steps vary a little bit. I'll outline what steps I did to get my setup working on Ubuntu 10.10.

Once you get vpnc setup and you are able to connect to it, all of your traffic should be routing through it by default.

1) vpnc was overwriting my /etc/resolv.conf file with nameservers on the VPN. To prevent this I set DNSUpdate no in my vpnc config file:
```

cat /etc/vpnc/myvpnc.conf

IPSec gateway publicdomain.example.com
IPSec ID XXXX
IPSec secret YYYY
Xauth username ZZZZZ
Xauth password *****

DNSUpdate no

```2) I then installed dnsmasq to handle resolving of domain names between my two sets of nameservers (local/ISP nameservers and the ones on the VPN for private domains):
```

sudo apt-get install dnsmasq

```3) Once dnsmasq is installed, you can edit it's config file at /etc/dnsmasq.conf
I needed to add a "server=" entry for my company's private domain. There should be a commented out line already:
```

server=/.privatedomain.example.com/192.168.0.1

```The first part is the private domain name and the second is the IP of the nameserver to use to lookup hosts on that domain. 

4) Set dnsmasq to only listen locally, I set the option "interface=lo", to only accept connections through the loopback interface, you can also use the "listen-address" option.

5) Make sure you're using your new nameserver (dnsmasq) that you've just setup.
I modified /etc/dhcp3/dhclient.conf, uncommenting the line beginning with "prepend"
```

prepend domain-name-servers 127.0.0.1;

```This will be sure that the default nameserver is your new local install of dnsmasq.

6) Restart networking with sudo /etc/init.d/networking restart. the first line in /etc/resolv.conf should now read:
```

nameserver 127.0.0.1

```I also have two more nameserver entries below that for my ISP that dnsmasq uses.

7) When you connect to your VPN, vpnc will set the default route to use tun0, routing all traffic through the VPN. You can see this with "netstat -r". To counter this you need to delete the route that vpnc adds, and add any routes that you need to go through the VPN.

Here is an example script that I have to connect my vpn (must be run as root, of course):
```

#!/bin/bash

echo "Connecting to myVPN..."
vpnc /etc/vpnc/myvpn.conf

echo "Setting up routing table..."
route del default dev tun0
route add -net 192.168.0.0 netmask 255.255.0.0 dev tun0

echo -n "Press Enter to continue..."
read

```

---

