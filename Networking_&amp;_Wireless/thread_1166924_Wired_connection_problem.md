---
title: "Wired connection problem"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by wigglesby85 on 2009-05-22
Hi

I've just installed Ubuntu and I cannot access the internet with a network cable.

The cable is plugged into the router, the same as my windows machine.

Can someone help me get online?

Thanks

---

### Post by i.r.id10t on 2009-05-22
Assuming your network card worked with the LiveCD, etc. 

I've noticed an issue with fresh installs of 9.04 and some network cards.  The default keyring messes things up wtih DHCP and the Network Manager applet.

Solution is to rm ~/.gnome2/keyrings/*

Before doing this, make sure your card can work "manually"

sudo dhclient eth0

---

### Post by wigglesby85 on 2009-05-22
That command gave me:

```

There is already a pid file /var/run/dhclient.pid with pid 14353
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:0c:76:24:55:88
Sending on   LPF/eth0/00:0c:76:24:55:88
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.21 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.21 from 10.0.0.2
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 10.0.0.21 -- renewal in 285459 seconds.

```

I can connect to the machine via ssh (putty) just the Ubuntu machine wont connect to the internet

---

### Post by brooklyn_83 on 2009-05-22
I had the same exact problem with a fresh install of kubuntu 8.04.Just got it fixed today. I tried about a MILLION different software attempts (editing /etc/network/ files) and no luck. Finally I turned off the desktop, unplugged the network card, and switched it to a different PCI slot. And BINGO it worked. I have no rational explanation as to why this worked. I seriously rebooted around 20 times before trying this. Good luck.

---

### Post by sedawk on 2009-05-22
Your PC has an IP (10.0.0.21), so everything seems to be fine!

The next step is to check the routing:
```

route

```
There should be something like "default 10.0.0.2"
This means every package that goes to the outside world will travel
via device 10.0.0.2 (packages to 10.0.0.* will travel only inside
your network).

If this entry is okay you should be able to "ping" outside IPs
like "ping a.b.c.d".
(If that server is pingable, otherwise it will not reply. Instead
of ping you can try to insert IPs in your browser, e.g.
[http://a.b.c.d](http://a.b.c.d), for a valid IP check below )

The next problem might be name resolution, mapping names to IPs.

Try "nslookup ubuntuforums.org".
Answer should be something like this:
Address: 91.189.94.12

If that works you should be able to browse
outside server, e.g. [http://ubuntuforums.org](http://ubuntuforums.org)

(Normally when you run "dhclient eth0" like you do you also
 get a valid router address and name server addresses, so if
 the reply of your DHCP-server is okay everything else should
 work out-of-the-box.)

---

### Post by wigglesby85 on 2009-05-22
From route I got the following:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     2      0        0 wlan0
default         10.0.0.2        0.0.0.0         UG    0      0        0 wlan0
default         10.0.0.2        0.0.0.0         UG    100    0        0 eth0

```

```

nslookup ubuntuforums.org
Server:         10.0.0.2
Address:        10.0.0.2#53

Non-authoritative answer:
Name:   ubuntuforums.org
Address: 91.189.94.12

```

I cannot ping anything to the outside world.

---

### Post by wigglesby85 on 2009-05-22
When I click on the little icon at the top (network connection settings) It says that the wired network device not managed.

How do I 'manage' it?

Thanks

---

### Post by Iowan on 2009-05-22
Is the wired network configured in /etc/network/interfaces - or was it configured in Network Manager?  NM has a "managed" setting in /etc/NetworkManager/nm-system-settings.conf.

---

### Post by superprash2003 on 2009-05-23
post output of ifconfig from the terminal, do you have firestarter or anything similar..also post output of
1)ping google.com
2)ping 208.67.222.222

---

### Post by superprash2003 on 2009-05-23
post output of ifconfig from the terminal, do you have firestarter or anything similar..also post output of
1)ping google.com
2)ping 208.67.222.222

---

### Post by sedawk on 2009-05-25
Have seen that before ;-)

Your wireless and wired network are connected to the same
network and that causes the trouble!
The easiest way is to disable one device!
Turn off wireless if you want to use the wired network or vice
versa.
As soon as the second device is gone and there is only one
default route everything should work fine.

(I never use the network manager - does it support "profiles"
 e.g profile "wired at home" and "wireless at home" or similar,
 so you can select the correct profile to use?
 I have seen something like that on MacOS ...)

---

