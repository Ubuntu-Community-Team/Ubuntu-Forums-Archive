---
title: "nic bonding problem"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by skynetcom on 2012-04-12
Hallo everybody,
 
i have the following problem:
Only one Nic is working. I have for e.g. 50% package lost if i use ping cmd. Fail over also doesnt work. I have allready tried everything i know.
 
Edit:
I am using ifnslave 2-6 
i tryed the following Modes
Mode 0 = Round Robin kein Failover 50% package lost 
Mode 6 = alb kein Failover 0% package lost 
I have no i dear why only one nic is working fine. If i interrutp the correct nic, everything works fine like a solo connecting. If i interrupt the other one, i lose the total connection.
If you need more information, just let me know :)
 
 
'''Hardware:'''
```
 
 
2600k, z68 mb, 8 GB ram
2x Realtake nic onboard (mii interface support)
 

``` 
 
'''Software:'''
```
 
 
Ubuntu 3.0.0-12-Server x86_64

``` 
 
Overview of my Settings:
 
root@insomnia:~# mii-tool'''
```
 
 
eth0: negotiated 1000baseT-FD flow-control, link ok
eth1: negotiated 1000baseT-FD flow-control, link ok
 

``` 
 
'''root@insomnia:~# modprobe --list |grep -i bonding'''
 
```
kernel/drivers/net/bonding/bonding.ko
```
 
 
'''root@insomnia:~# cat /etc/network/interfaces'''
 
```
 
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet manual
bond-master bond0
bond-primary eth0 eth1
##dhcp eth0
#iface eth0 inet dhcp
# address 192.168.100.200
# netmask 255.255.255.0
# gateway 192.168.100.1
# network 192.168.100.0
# broadcast 168.168.100.255
 
auto eth1
iface eth1 inet manual
bond-master bond0
bond-primary eth0 eth1
##static eth1
#iface eth1 inet static
# address 192.168.100.201
# netmask 255.255.255.0
# gateway 192.168.100.1
# network 192.168.100.0
# broadcast 168.168.100.255
### Adapter bonding for eth0 and eth1
auto bond0
iface bond0 inet static
address 192.168.100.200
netmask 255.255.255.0
gateway 192.168.100.1
bond-miimon 100
bond-mode 0
bond-slaves none

```
 
waiting for some help ):P

---

### Post by skynetcom on 2012-04-24
not even a single idear?

---

### Post by skynetcom on 2012-04-29
i have tried a intel dual port Gigabit nic. It works fine. Is there a nic setting i have to change on both Realtake onboard nic? On windows teaming works fine with the onboard nic.
 
any idears?

---

### Post by skynetcom on 2012-05-22
Got it, the default drive wich is used by Ubuntu was wrong,
I download the newest version vom the Realtake hompage, compiled it, and every thing works perfekt now ^^.
 
I got an MSI z68 GD80 MB with 2 Realtake 8111E onboard
 
i changed driver from r...69 to r...68

---

