---
title: "Set Static IP by Network Manager but reverted back to DHCP"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-04-19
Hi,

Using Ubuntu 8.10 x64. I would like to use a static IP to access samba shared folder (so the computer is always the same).

Panel top right, right click on the Network Manager icon. Select "Edit Connections"

- Edit Auto eth0, IPv4 properties.
- Changed Mode from "Automatic DHCP to Manual
- Set IPs for IP Address, Subnet, Gateway, DNS Servers. I make sure I use an IP outside of the DHCP range of the router.

After the computer is rebooted, all the Static IP info are lost. The settings reverted back to DHCP.

Q1. Was it a bug or the standard way to set static IP is to edit the /etc/network/interfaces file and removing the dhcp-client as instructed in this tutorial [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

Q2. May be there is a better way to access samba shared folder without using a static IP?

Thanks in advance for any help.

---

### Post by doas777 on 2009-04-19
I had the same problem. the easiest answer was to delete "Auto eth0" from your network manager and create a new profile (called eth0). If that doesn't work for you, the other common fix is to configure it in your /etc/network/interfaces file, as you have already discovered. no there is no good reason that it works this way, at least that I can discern.

---

### Post by Iowan on 2009-04-19
> **UranUtan said:**
> 
Q2. May be there is a better way to access samba shared folder without using a static IP?Dunno if it's better...
Another option is to let the machine get DHCP address, but set up a "static lease" (based on MAC address) in the DHCP server - if the DHCP server is capable...

---

### Post by UranUtan on 2009-04-19
> **Iowan said:**
> Dunno if it's better...
Another option is to let the machine get DHCP address, but set up a "static lease" (based on MAC address) in the DHCP server - if the DHCP server is capable...

My router can do that. However I find this less elegant than static IP because part of the settings will rely on the router. And I am afraid one day I will forget about this (reset router, change for new router, etc.)

I followed doas777's advice, delete Auto eth0 and recreate a new one works perfectly. May be not very geek but I find this easier to remember than manually editing files.

---

### Post by doas777 on 2009-04-20
I find that for servers, it just best to statically address. no point in adding the complexity of configuring mac caching, or dynamic registration, unless you are doing high-availability, or load balenced services.

glad that worked for ya. I too found it to be the simplest fix.

good luck,
franklin

---

### Post by Iowan on 2009-04-20
Some folks like the simplicity of managing all IP addresses from one machine, but to each his own... glad you got it working!

---

