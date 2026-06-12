---
title: "VPN with pptpd  &amp; Windows Clients"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by JerryTom on 2011-05-17
I have a 10.10 32bit server running Apache/Bind/PPTPD on VMware ESX 4.1

Ubuntu VPN
IP: 22.22.22.22
NETMASK: 255.255.255.224
BROADCAST: 22.22.22.31
GATEWAY: 22.22.22.1

Windows XP Client
IP: 112.232.10.10
NETMASK: 255.255.255.192
GATEWAY: 112.232.10.1
DNS: 22.22.22.22

Given the above systems they can ping each other. There is an ACL that prevents the XP client from accessing apache unless it's on the 22.22.22.x network.

Using the built-in VPN connection in XP I created a setup to connect to the Ubuntu VPN server and it connects just fine and get's an IP address as follows:

IP: 22.22.22.2
NETMASK: 255.255.255.255
GATEWAY: 22.22.22.2

When connected to the VPN I cannot access the web page hosted on the VPN server but I can ping everything. When the ACL is turned off the apache log shows the access as coming from the client's local IP of 112.232.10.10 and not the VPN. This is the problem and I am stumped on how to resolve.

The pptpd.conf is default except;
localip 22.22.22.22
remoteip 22.22.22.2-21

pptpd-options is all default as well

I changed /etc/default/ufw DEFAULT_FORWARD_POLICY to ACCEPT
/etc/ufw/before.rules I added:

*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 22.22.22.0/27 -o eth0 -j MASQUERADE
COMMIT

in the filter section;
-A ufw-before-input -i ppp+ -j ACCEPT
-A ufw-before-output -i ppp+ -j ACCEPT
-A ufw-before-forward -s 22.22.22.0/27 -j ACCEPT
-A ufw-before-forward -d 22.22.22.0/27 -j ACCEPT
COMMIT

I set net.ipv4.ip_forward=1 in /etc/ufw/sysctl.conf
UFW is set to start at boot

Any ideas and is there anything additional information I should provide? All this is in our lab and I did not pick the IP schemes, I was brought in to build a Linux box and provide Web/DNS/VPN services for the staff to use for teaching purposes.

Thanks!

---

