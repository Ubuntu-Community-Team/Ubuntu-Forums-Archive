---
title: "Anybody get ike working under 10.10?"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by bing on 2010-10-19
Hi,

Shrew Soft ike was working fine under ubuntu 9.10 x86 but can't seem to get it working under 10.10. The imported .pcf file works fine under Windows ike 2.1.6 and 2.1.7.

Has anybody gotten it working? I already did the usual rp_filter = 0 business but I'm not sure there isn't another filter I'm missing(see output below).

Thanks!

Problem:
The VPN client 2.1.5 default repo .deb package and freshly compiled 2.1.7 connect successfully and receives the welcome message but any subsequent internet activity times out. 

To Reproduce:
VPN client 2.1.7
OS Ubuntu 10.10 x86 (32-bit)
Gateway Make = Cisco VPN 3000
Gateway OS Version = unknown

Modified /etc/sysctl.conf and /etc/sysctl.d/10-network-security.conf to *.rp_filter=0.

sudo sysctl -a | grep rp_filter | grep -v arp
error: "Invalid argument" reading key "fs.binfmt_misc.register"
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 1
net.ipv4.conf.eth1.rp_filter = 1

---

### Post by zeronez on 2010-10-22
Problem:
The VPN client 2.1.5 default repo .deb package and freshly compiled  2.1.7 connect successfully and receives the welcome message but any  subsequent internet activity times out. 


Modified /etc/sysctl.conf and /etc/sysctl.d/10-network-security.conf to *.rp_filter=0.

sudo sysctl -a | grep rp_filter | grep -v arp
error: "Invalid argument" reading key "fs.binfmt_misc.register"
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 1
net.ipv4.conf.eth1.rp_filter = 1 

Hmm, I had a similar issue running 10.04 release, where I would get connection to the VPN server but after about 5-10 min the connection would hang up, and I couldn't receive any inbound traffic. 

What I did to resolve it was that I uncommented the following lines from the network-security-conf instead of trying to change the filter to 1 or 0: 

<snip>
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks.
[U]# net.ipv4.conf.default.rp_filter=1
# net.ipv4.conf.all.rp_filter=1[/U]

You might also want to try to uncomment the eth0, eht1 and lo and testing to see if your connection works. 

I wouldn't be too worried of these messages: 

error: "Invalid argument" reading key "fs.binfmt_misc.register"
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'

As I get them too if I try to grep those files..

hope this helps:)

---

### Post by observer1 on 2010-11-01
Good old Cisco VPN 3000 - too bad they discontinued them :(

Are you sure that you made all settings correct? Because if you did, all results of the 
sudo sysctl -a | grep rp_filter | grep -v arp 
should be = 0.

I  upgraded from 10.04 to 10.10, which replaced my customized /etc/sysctl.conf. After editing it according to the Shrew FAQ, it worked again.

---

### Post by A4orce84 on 2011-01-24
Is there good documentation on how to install Shrew Soft VPN Client in Ubuntu somewhere? Tried googling, came up with nothing.

---

### Post by observer1 on 2011-01-25
sudo apt-get install iked?

---

