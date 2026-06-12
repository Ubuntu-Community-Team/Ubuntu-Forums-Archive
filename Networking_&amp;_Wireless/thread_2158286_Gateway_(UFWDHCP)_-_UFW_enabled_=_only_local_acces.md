---
title: "Gateway (UFW/DHCP) - UFW enabled = only local access for network machines."
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by krs360 on 2013-06-28
[FONT=arial][SIZE=2]Hello all,

I've been using various distros such as ClearOS/IPFire and BSD ones like m0n0wall and Pfsense. Anyway, I decided to simply drop to Ubuntu and create some rules myself.

So far:

I've installed Ubuntu 13.04
Installed ISC DHCP server and configured as necessary.
[/SIZE][/FONT]NICS as follows:
eth0      Link encap:Ethernet inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
eth1      Link encap:Ethernet inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0

[FONT=arial][SIZE=2]I've run:

[/SIZE][/FONT][FONT=arial][SIZE=2]iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE
[/SIZE][/FONT][FONT=arial][SIZE=2]iptables --append FORWARD --in-interface eth0 -j ACCEPT[/SIZE][/FONT] 

[FONT=arial][SIZE=2]Also added the forward of:
[/SIZE][/FONT][FONT=arial][SIZE=2]echo 1 > /proc/sys/net/ipv4/ip_forward   

This provides me with a working connection from all of the machines assigned by DHCP (with UFW disabled). 
Upon enabling UFW it blocks all internet based access, but allows local access.

Here is what /var/log/kern.log looks like when I attempt to search google for something..

Jun 28 15:38:02 firewall kernel: [  775.477477] [UFW BLOCK] IN=eth1  OUT=eth0 MAC=XXXXXXXXXX SRC=8.8.4.4 DST=192.168.2.10 LEN=140 TOS=0x00  PREC=0xA0 TTL=48 ID=37356 PROTO=UDP SPT=53 DPT=60659 LEN=120

I'm guessing the data is coming back from google but not being blocked from being sent to the local machine?

Other information:[/SIZE][/FONT]
root@firewall:~# ufw status verbose
Status: active
Logging: on (high)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       192.168.2.0/24
80                         ALLOW       Anywhere
53                         ALLOW       Anywhere
80                         ALLOW       Anywhere (v6)
53                         ALLOW       Anywhere (v6)
root@firewall:~#

[FONT=arial][SIZE=2]Have I done something really stupid, or have I missed out something?

Thanks.

[/SIZE][/FONT] [FONT=arial][SIZE=2]
[/SIZE][/FONT]

---

### Post by krs360 on 2013-06-28
This has been resolved now, missed a one liner for forwarding.

---

