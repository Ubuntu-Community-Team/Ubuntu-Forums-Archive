---
title: "dhclient problem"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by rusayub on 2010-03-24
Hello.

I have a quite strange trouble with dhcp3-client.
My network interfaces are eth0 and eth1, first uses dhcp to get ip etc, second has static ip.

/etc/network/interfaces:

auto lo eth0 eth1

iface lo inet loopback
 address 127.0.0.1
 netmask 255.0.0.0

iface eth0 inet dhcp
 #address 10.235.72.129
 #netmask 255.255.248.0
 #gateway 10.235.72.1
 #broadcast 10.235.79.255

iface eth1 inet static
 address 192.168.1.50
 netmask 255.255.255.0
 gateway 192.168.1.50
 broadcast 192.168.1.255

But i can see dhclient trying to get ip for eth1:

/var/log/syslog:

port 67 interval 4
Mar 25 01:09:00 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Mar 25 01:09:04 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Mar 25 01:09:10 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Mar 25 01:09:23 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Mar 25 01:09:32 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Mar 25 01:09:43 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Mar 25 01:09:51 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2

Any ideas?

---

### Post by Iowan on 2010-03-24
My */etc/network/interfaces* file doesn't list address and subnet mask for "lo" - but that's *probably* not the issue...
Does this machine have Network Manager running? if so, you might check */etc/NetworkManager/system-connections* to see if there's a file for eth1. If so, it may be overriding your *interfaces* file. You might delete, rename or move that file (caution would suggest saving it *somewhere*), and reboot/restart. Another option would be to use NM to create the manual configuration.

---

### Post by rusayub on 2010-03-24
ls /etc/NetworkManager
dispatcher.d  nm-system-settings.conf

So there's no eth1 file.

---

### Post by rusayub on 2010-03-24
btw the last dhclient bcast on eth1:

Mar 25 01:09:51 cyberchondiac dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2

Now its ok. I do not want to use NM to create the manual configuration. I removed NM right after the install.

---

### Post by Iowan on 2010-03-24
Guess I didn't ask what version you're running...
If NM is removed, you may need to **purge** it, too - it would seem that some files got left behind. NM is supposed to execute the scripts in *etc/NetworkManager/dispatcher.d*, and the settings in */etc/NetworkManager/nm-system-settings.conf* (on my Jaunty laptop) list some defaults. 
You'd think this would all be neutralized without NM, but...

---

### Post by rusayub on 2010-03-26
I purged NM, but the problem is actual again: (syslog)

Mar 27 00:30:49 cyberchondiac dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Mar 27 00:30:49 cyberchondiac dhcpd: DHCPREQUEST for 192.168.1.102 from 00:e0:4d:05:09:b0 via eth1
Mar 27 00:30:49 cyberchondiac dhcpd: DHCPACK on 192.168.1.102 to 00:e0:4d:05:09:b0 via eth1
Mar 27 00:31:00 cyberchondiac dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Mar 27 00:31:00 cyberchondiac dhcpd: DHCPREQUEST for 192.168.1.102 from 00:e0:4d:05:09:b0 via eth1

I can not undestand what app starts dhclient now.

---

