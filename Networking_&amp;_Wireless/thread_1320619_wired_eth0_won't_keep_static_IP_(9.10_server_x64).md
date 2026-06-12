---
title: "wired eth0 won't keep static IP (9.10 server x64)"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by chrisvo on 2009-11-09
Hi all,

I've configured eth0 on my 9.10 x64 server with static IP. It works beautifully for about 15-30 minutes, then for some reason decides to request a new DHCP address, overwriting the static IP configuration. If I ifdown/ifup again, it goes back to the static IP that I configured in the first place. Does anyone have an idea why Ubuntu might be doing this? 

Here's my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.23
netmask 255.255.255.0
gateway 10.0.0.1
```uname:
```
Linux 2.6.31-14-server #48-Ubuntu SMP x86_64 GNU/Linux
```lspci:
```
03:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```/var/log/messages entries that appear when the server does this (that's all, there are no other messages that appear in dmesg or /var/log/messages at the time the IP address resets). BTW, 10.0.0.23 is the desired static address; 10.0.0.105 is the address it ends up getting via DHCP...
```
Nov  9 11:30:33 aurora dhcpd: DHCPDISCOVER from 00:30:48:ba:01:64 via eth0
Nov  9 11:30:33 aurora dhcpd: DHCPOFFER on 10.0.0.23 to 00:30:48:ba:01:64 via eth0
Nov  9 11:30:33 aurora dhcpd: DHCPREQUEST for 10.0.0.23 (10.0.0.105) from 00:30:48:ba:01:64 via eth0
Nov  9 11:30:33 aurora dhcpd: DHCPACK on 10.0.0.23 to 00:30:48:ba:01:64 via eth0
```Thanks for any help!

-- Christopher Vo

---

### Post by chrisvo on 2009-11-09
Solved.

I changed from DHCP to Static IP configuration, but of course this does not kill dhclient, which was still running and trying to obtain a new IP address :oops:. I killed the dhclient process and now everything runs beautifully. :D

---

### Post by tiras_dude on 2009-11-26
would you be so kind to provide the command with wich you killed the dhclient?

---

### Post by Iowan on 2009-11-26
```
ps -ef |grep dhclient
``` should show if it's running, and give the PID of the program that called it.
Short term, you can **kill** dhclient, but long term, you'll want to stop it from getting called.

---

