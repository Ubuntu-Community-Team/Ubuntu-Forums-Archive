---
title: "Ethernet connection help needed, please!"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by Lazlo Woodbine on 2009-08-04
After losing network connectivity (which turned out to be the cable company's issue - grrr), I deleted the working "auto eth0" connection, thinking that Ubuntu would recreate it and all would be working again. Unfortunately, it isn't. 

An "Auto ethernet" connection has been created, and the tray icon reports that I am connected to it. This connection appears to be complete, with an IP address and DNS servers set up. The only problem is that *it doesn't work*. It has absolutely NO connectivity whatsoever. I cannot connect to the router using its IP address, let alone connect to the internet using a URL. 

Bizarrely, although the eth0 connection appears when using ifconfig, absolutely minimal traffic seems to be using it, whilst the loopback connection is extremely busy. Comparing this to my wife's computer, which is connected to the same router it looks almost as if all traffic that should be going through eth0 is going through loopback instead. Is this possible?

The tray icon also has a different appearance to that on my wife's laptop. Hers shows the one computer in front of another, whereas mine adds a right-angled connection between these two in the bottom right hand corner. 

I'm not a complete novice when it comes to networking, but neither am I an expert, and this has me completely stumped. Please help!

---

### Post by Iowan on 2009-08-04
The right-angle connection sounds like wireless... (or maybe it's part of a slash... meaning no connection.) What happens if you click on the icon - does it show wired connection as "disconnected"?
Check result of **route -n** - the default gateway should have a "ug" (besides probably being last on the list.) and *should* show eth0.

---

### Post by Lazlo Woodbine on 2009-08-04
route - n is showing the following:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0       0.0.0.0           255.255.255.0     U       1        0        0 eth0
169.254.0.0       0.0.0.0           255.255.0.0       U       1000     0        0 eth0
0.0.0.0           192.168.2.1       0.0.0.0           UG      0        0        0 eth0

This is identical to the working setup on my wife's laptop. 


Disabling wireless doesn't change the icon, so I don't think it's that.

---

### Post by Iowan on 2009-08-04
Post result of **ifconfig -a**.

---

### Post by Lazlo Woodbine on 2009-08-04
ifconfig -a

eth0

      Link encap:Ethernet  HWaddr 00:1d:09:26:0f:d8  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe26:fd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5090 (5.0 KB)  TX bytes:3365 (3.3 KB)
          Memory:fbfe0000-fc000000 


lo

        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:260357 (260.3 KB)  TX bytes:260357 (260.3 KB)


pan0

      Link encap:Ethernet  HWaddr ca:20:aa:fa:8c:9d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0

     Link encap:Ethernet  HWaddr 00:1e:8c:60:66:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wmaster0

  Link encap:UNSPEC  HWaddr 00-1E-8C-60-66-2F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



I think I'm seeing that eth0 traffic is minimal, whilst lo seems much higher than it should be. It's as if these two interfaces have been switched. Is that possible?!

---

### Post by latev on 2009-08-04
what's the output of

mii-tool
ping 192.168.2.1
cat /etc/resolv.conf
cat /etc/network/interfaces
ifdown eth0
ifup eth0
/etc/init.d/networking restart


in the same order

---

### Post by Lazlo Woodbine on 2009-08-04
$ mii-tool

SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found



$ sudo mii-tool

SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
eth0: negotiated 100baseTx-FD flow-control, link ok



$ ping 192.168.2.1

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted



$ cat /etc/resolv.conf

# Generated by NetworkManager
domain Belkin
search Belkin
nameserver 192.168.2.1
nameserver 68.87.74.166
nameserver 68.87.68.166



$ cat /etc/network/interfaces

auto lo
iface lo inet loopback



$ ifdown eth0

ifdown: failed to open statefile /var/run/network/ifstate: Permission denied


$ sudo ifdown eth0

Ignoring unknown interface eth0=eth0.



ifup eth0

ifup: failed to open statefile /var/run/network/ifstate: Permission denied



$ sudo ifup eth0

Ignoring unknown interface eth0=eth0.
 


$ /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                          ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
                                                                                                         [fail]



$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                   [ OK ]

---

### Post by Lazlo Woodbine on 2009-08-04
Thanks very much for taking the time to look at my problem, by the way, to both Iowan and latev.

---

### Post by latev on 2009-08-04
1) Add the following lines to your interfaces file

auto eth0
iface eth0 inet dhcp


2) Paste the following into a say flushiptables.sh file, make it executable, run it as root

#!/bin/sh
#
# rc.flush-iptables - Resets iptables to default values.
#
# Copyright (C) 2001  Oskar Andreasson <bluefluxATkoffeinDOTnet>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program or from the site that you downloaded it
# from; if not, write to the Free Software Foundation, Inc., 59 Temple
# Place, Suite 330, Boston, MA  02111-1307   USA

#
# Configurations
#
IPTABLES="/sbin/iptables"

#
# reset the default policies in the filter table.
#
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT

#
# reset the default policies in the nat table.
#
$IPTABLES -t nat -P PREROUTING ACCEPT
$IPTABLES -t nat -P POSTROUTING ACCEPT
$IPTABLES -t nat -P OUTPUT ACCEPT

#
# reset the default policies in the mangle table.
#
$IPTABLES -t mangle -P PREROUTING ACCEPT
$IPTABLES -t mangle -P OUTPUT ACCEPT

#
# flush all the rules in the filter and nat tables.
#
$IPTABLES -F
$IPTABLES -t nat -F
$IPTABLES -t mangle -F
#
# erase all chains that's not default in filter and nat table.
#
$IPTABLES -X
$IPTABLES -t nat -X
$IPTABLES -t mangle -X


3) as root again run
ifdown eth0
ifup eth0
ping 192.168.2.1
arp

hope it helps
/the script brings down your firewall, you may have to bring it up afterwards if needed/

---

### Post by Lazlo Woodbine on 2009-08-04
> **latev said:**
> 1) Add the following lines to your interfaces file

auto eth0
iface eth0 inet dhcp



My wife's laptop, connected to the same router, does NOT have these lines in this file, and works perfectly. Please could you explain why you think I should need them?


> 
2) Paste the following into a say flushiptables.sh file, make it executable, run it as root

#!/bin/sh
#
# rc.flush-iptables - Resets iptables to default values.
#
# Copyright (C) 2001  Oskar Andreasson <bluefluxATkoffeinDOTnet>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program or from the site that you downloaded it
# from; if not, write to the Free Software Foundation, Inc., 59 Temple
# Place, Suite 330, Boston, MA  02111-1307   USA

#
# Configurations
#
IPTABLES="/sbin/iptables"

#
# reset the default policies in the filter table.
#
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT

#
# reset the default policies in the nat table.
#
$IPTABLES -t nat -P PREROUTING ACCEPT
$IPTABLES -t nat -P POSTROUTING ACCEPT
$IPTABLES -t nat -P OUTPUT ACCEPT

#
# reset the default policies in the mangle table.
#
$IPTABLES -t mangle -P PREROUTING ACCEPT
$IPTABLES -t mangle -P OUTPUT ACCEPT

#
# flush all the rules in the filter and nat tables.
#
$IPTABLES -F
$IPTABLES -t nat -F
$IPTABLES -t mangle -F
#
# erase all chains that's not default in filter and nat table.
#
$IPTABLES -X
$IPTABLES -t nat -X
$IPTABLES -t mangle -X


3) as root again run
ifdown eth0
ifup eth0
ping 192.168.2.1
arp

hope it helps
/the script brings down your firewall, you may have to bring it up afterwards if needed/


Just ran your iptables flushing script, went away, and when I came back I was back online. 

Thank you very much for your help!

[EDIT] Note that I did NOT make the alterations to my interfaces file that you had suggested.

---

### Post by latev on 2009-08-04
glad you're back in the matrix again ;)

Having eth0 defined in interfaces would have made ifup, ifdown happy

$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.

---

### Post by Iowan on 2009-08-04
> **latev said:**
> Having eth0 defined in interfaces would have made ifup, ifdown happy. Might have made Network Manager unhappy, but it would be a small price for working system.  I've seen that "operation not permitted" message before - hope I can remember the IPtables flush when I see the message next time.

---

