---
title: "Ruined DHCP. How to restore it?"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by jazzgossen on 2010-06-01
In an attempt to get a Huawei E620 GSM modem to work, I installed the trunk version of network-manager from [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu)

However, that seems to have broken the DHCP client. This was on Ubuntu 9.10. I have since removed the PPA packages using ppa-purge, and upgraded to Ubuntu 10.04. But I still can't use DHCP. The wired connection that I'm using at the moment, with a static IP, works fine.

This snippet from the syslog when I try to connect to a wireless network with DHCP looks a bit weird, I think?
```
Jun  1 05:44:14 lateralus dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun  1 05:44:14 lateralus dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun  1 05:44:14 lateralus dhclient: All rights reserved.
Jun  1 05:44:14 lateralus dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  1 05:44:14 lateralus dhclient: Usage: dhclient [-1dqrx] [-nw] [-p <port>] [-s server]
Jun  1 05:44:14 lateralus dhclient:                 [-cf config-file] [-lf lease-file][-pf pid-file] [-e VAR=val]
Jun  1 05:44:14 lateralus dhclient:                 [-sf script-file] [interface]

```

---

### Post by moody_mark on 2010-06-01
What happens if you just type "dhclient" in a terminal?

---

### Post by jazzgossen on 2010-06-01
That looks better:

```
$ sudo dhclient

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/xxxxxxx
Sending on   LPF/wlan0/xxxxxxx
Listening on LPF/eth0/xxxxxxx
Sending on   LPF/eth0/xxxxxxx
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
...

```

I'll see what I can do with this once I get home.

---

### Post by jazzgossen on 2010-06-02
Allright, running "sudo dhclient wlan0" does give me an IP address for the wireless DHCP network. 

Now the question is, how to get it done automatically. 

By the way, the nm-applet icon still pulses as when it is trying to connect, even though I do have an established connection right now.

---

### Post by Iowan on 2010-06-02
Any extra lines in */etc/netowrk/interfaces*? It should only have the two defining "lo" in a standard NM-controlled machine.

---

### Post by jazzgossen on 2010-06-02
No, just "auto lo" and "iface lo inte loopback".

---

### Post by jazzgossen on 2010-06-02
I just installed wicd and removed network-manager, and that works for now. However, I would like to get network-manager to work again so that I can also use GSM modems.

---

### Post by jazzgossen on 2010-06-13
Allright, reinstalling network-manager fixed my problem. I have now removed wicd, and everything works as it should again. Thanks for your input, all.

---

