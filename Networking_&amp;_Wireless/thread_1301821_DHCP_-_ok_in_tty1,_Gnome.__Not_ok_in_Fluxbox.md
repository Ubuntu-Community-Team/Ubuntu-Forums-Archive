---
title: "DHCP - ok in tty1, Gnome.  Not ok in Fluxbox"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by Her Ghost on 2009-10-26
Hey,

When I am in Gnome, nm-applet manages my wifi connections fine.  No problems at all.  Additionally, if I kill nm-applet and manually connect using:

```
sudo ifconfig eth1 up
iwconfig eth1 essid MYNETNAME
iwconfig eth1 kay MYNETKEY
sudo dhclient
```

It is fine.

If I kill the connection and try again from tty1, then it's fine too.

If I kill the connection and boot into Fluxbox instead of Gnome, then I have problems (detail below).  If, however, I boot into Fluxbox and run nm-applet it's fine!

Any ideas on what is happening here?  Suggestions?

Thanks!

output from dhclient when run through Fluxbox:

```
There is already a pid file /var/run/dhclient.pid with pid 4050
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/a2:78:3e:c4:64:67
Sending on   LPF/pan0/a2:78:3e:c4:64:67
Listening on LPF/eth1/00:0e:35:1b:40:36
Sending on   LPF/eth1/00:0e:35:1b:40:36
Listening on LPF/eth0/00:0e:7b:59:4c:06
Sending on   LPF/eth0/00:0e:7b:59:4c:06
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST of 192.168.0.5 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 192.168.0.5 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
herghost@herghost-laptop:~$ 
```

I'm on a Toshiba Tecra laptop, running 9.04.

---

### Post by ScarySquirrel on 2010-04-23
"If I kill the connection and boot into Fluxbox instead of Gnome"
What, exactly, do you mean by this? Do you mean by pressing ctrl alt backspace?

---

