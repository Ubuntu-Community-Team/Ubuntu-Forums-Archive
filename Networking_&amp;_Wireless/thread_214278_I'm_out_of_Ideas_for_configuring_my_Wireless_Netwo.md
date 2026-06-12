---
title: "I'm out of Ideas for configuring my Wireless Network Adapter Model: WMP54GX"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Tygger on 2006-07-12
I've been trying for several days to get my Wireless Network Adapter to work using information I've gleaned from these forums and the wiki.

The chipset for my card is:

```

Airgo Networks Inc 17CD:0001

```
and so I installed the driver that corresponded with this chipset using ndiswrapper.

I've installed WiFi Radar and it finds my Wireless Router.  When I connect to it though I do not get an IP address unless I have a wired connection to the router.

I've tried editing /etc/network/interfaces and specifying the following:

```

auto wlan0
iface wlan0 inet dhcp
wireless-essid PANCP08202005
wireless-key xxxxxxxxxx
wireless-keymode open
wireless-mode managed

```

Whenever I turn off the wired connection using:

```

sudo ifdown eth0

```

I cannot obtain an ip address using:

```

sudo dhclient wlan0

```

This is the output I receive:

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:12:17:8f:34:72
Sending on   LPF/wlan0/00:12:17:8f:34:72
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
bogus UDP packet length: 556
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I'm fresh out of ideas.  Has anyone been successful in getting this particular adapter to work with ndiswrapper?  Does anyone have further suggestions I might try?

I'm new to Linux and these forums have been invaluable in getting other things to work.  This wireless network thing just has me stumped.

Thanks for your help.
Andy Mason

---

### Post by davmac on 2007-07-02
Andy,

Can't believe I stumbled across you here! Are you still having the problem?

Dave Mac

---

### Post by kevdog on 2007-07-02
Looks like you have done your homework and Im not sure if Im going to be any better at it than you.

Recommendations
Turn off WEP for now -- can you connect??

Can you post the following
lshw -C network
lspci
iwlist scan
ndiswrapper -v
ndiswrapper -l

What I would also try is to remove the driver:
sudo modprobe -r ndiswrapper
Insert back into kernel
sudo modprobe -i ndiswrapper

Then check dmesg for any error message after the reinsertion.  You could post the results here, however dmesg is the complete boot log, and only the sections related to ndiswrapper, wireless are needed.

---

### Post by imdano on 2007-07-02
Are you able to connect if you specify a static IP?

edit: Just noticed this post is a year old...

---

