---
title: "Network fails on reboot"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by wombat20 on 2006-06-25
I'm using a Connexant ethernet wired router, which works fine with 2 other machines and my onboard nVidia network which seems fine in XP.

The problem is that my network (from this machine only) disappears whenever I reboot.
Some Info
```
james@dappercow:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0

```
```
james@dappercow:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
james@dappercow:~$ cat /etc/resolv.conf
domain home
nameserver 10.0.0.2
james@dappercow:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

Everything works nicely after I do:
```
james@dappercow:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:14:85:19:a4:45
Sending on   LPF/eth0/00:14:85:19:a4:45
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.10 -- renewal in 40659 seconds.
```

I don't know why it's sending the request to 255.255.255.255.

Then I get:
```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG        0 0          0 eth0

```

Is there any way I can set this up to work automatically on bootup?  Is there a config file I should edit and a guide as to what I should put in it.

Any suggestions appreciated.  :D

---

### Post by wombat20 on 2006-06-25
Just found the answer to my own problem.  Goes to show I should search harder first.

[http://www.ubuntuforums.org/showthread.php?t=133599](http://www.ubuntuforums.org/showthread.php?t=133599)

The solution has been edited into the first post.

**_Worth noting however, that:_**
```
 for router in $new_routers; do
```
appears twice in the **dhclient-script** file, and you have to get both occurrences!

---

