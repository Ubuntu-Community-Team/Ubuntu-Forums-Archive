---
title: "OpenVPN for 9.04 Ubuntu"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by ninja123 on 2010-07-28
Hi All,

I am simulating a VPN connection and therefore my test setup looks like the following:

Ubuntu 9.04 (host) machine with Virtual box having another ubuntu 9.04 VM(let's call it VM)

VM should connect to Host via VPN.

I installed OpenVPN on both machines and for my purpose set up VPN in tunnel mode(NO bridging) and hence followed PART 1 of this link:


[http://ubuntuforums.org/showthread.php?t=752127]("http://ubuntuforums.org/showthread.php?t=752127")

Sadly, I get:

read UDPv4 [EHOSTUNREACH]: No route to host (code=113)


My IPs are as follows:

Host:

eth0: 192.168.1.100
tun0: 10.0.0.1
vboxnet0: Has no IP

VM:

eth0:192.168.1.150
tun0: 10.0.0.2


Please help.


My config scripts for openvpn look like:

_On Host:_

dev tun0
remote 192.168.1.150
ifconfig 10.0.0.1 10.0.0.2
secret /etc/openvpn/static.key
daemon

lport 15000
rport 1194

user nobody
group nogroup
persist-key
persist-tun

verb 3

ping-restart 60
ping 20


 _On VM:_
dev tun0
remote 192.168.1.100
ifconfig 10.0.0.2 10.0.0.1
secret /etc/openvpn/static.key
daemon

lport 15000
rport 1194

user nobody
group nogroup
persist-key
persist-tun

verb3

ping-restart 60
ping 20


After this I cant ping between 10.0.0.1 and 10.0.0.2 as I get the above "No route to host" error.


Please help.

Has it anything to do with the virtual box networking configuration?

---

