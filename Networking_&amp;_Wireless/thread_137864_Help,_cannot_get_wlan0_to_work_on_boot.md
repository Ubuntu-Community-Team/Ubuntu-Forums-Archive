---
title: "Help, cannot get wlan0 to work on boot"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by Eyebolt on 2006-02-28
So i'm farther than I was yesterday...

I can now get my WG111v2 to work...but not at boot up. I can only get it to work after doing this:

sudo invoke-rc.d network restart
sudo dhclient wlan0

Before that, I don't have an IP. So I want my machine to obtain an IP during boot up and not need me to type those command in everytime.

Here's the dump of the syslog while I did the invoke-rc.d command:
Feb 28 20:03:16 localhost dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 6697
Feb 28 20:03:16 localhost dhclient: killed old client process, removed PID file
Feb 28 20:03:16 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb 28 20:03:16 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb 28 20:03:16 localhost dhclient: All rights reserved.
Feb 28 20:03:16 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Feb 28 20:03:16 localhost dhclient:
Feb 28 20:03:16 localhost dhclient: sit0: unknown hardware address type 776
Feb 28 20:03:16 localhost dhclient: sit0: unknown hardware address type 776
Feb 28 20:03:16 localhost dhclient: Listening on LPF/wlan0/00:0f:b5:d4:56:98
Feb 28 20:03:16 localhost dhclient: Sending on   LPF/wlan0/00:0f:b5:d4:56:98
Feb 28 20:03:16 localhost dhclient: Sending on   Socket/fallback
Feb 28 20:03:16 localhost dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Feb 28 20:03:16 localhost dhclient: send_packet: Network is unreachable
Feb 28 20:03:16 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Feb 28 20:03:16 localhost dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Feb 28 20:03:16 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb 28 20:03:16 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb 28 20:03:16 localhost dhclient: All rights reserved.
Feb 28 20:03:16 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Feb 28 20:03:16 localhost dhclient:
Feb 28 20:03:16 localhost dhclient: sit0: unknown hardware address type 776
Feb 28 20:03:16 localhost dhclient: sit0: unknown hardware address type 776
Feb 28 20:03:16 localhost dhclient: Listening on LPF/wlan0/00:0f:b5:d4:56:98
Feb 28 20:03:16 localhost dhclient: Sending on   LPF/wlan0/00:0f:b5:d4:56:98
Feb 28 20:03:16 localhost dhclient: Sending on   Socket/fallback
Feb 28 20:03:18 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Feb 28 20:03:23 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Feb 28 20:03:23 localhost dhclient: DHCPOFFER from 192.168.1.1
Feb 28 20:03:23 localhost dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Feb 28 20:03:24 localhost dhclient: DHCPACK from 192.168.1.1
Feb 28 20:03:24 localhost dhclient: bound to 192.168.1.101 -- renewal in 35282 seconds.
Feb 28 20:03:27 localhost kernel: [ 1032.746775] wlan0: no IPv6 routers present
Feb 28 20:17:01 localhost /USR/SBIN/CRON[8607]: (root) CMD (   run-parts --report /etc/cron.hourly)

here is my current interfaces file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script echo
	map wlan0

# The primary network interface
iface wlan0 inet dhcp
wireless-channel 11
wireless-mode Managed
wireless-essid XXXXX
wireless-key XXX-XXXX-XX
auto wlan0



Any ideas??? I really need to get this going so I can make this into my mythbox.

---

### Post by aosmith on 2006-02-28
maybe write a bash script that runs @ login to do it for you?

---

### Post by Eyebolt on 2006-02-28
I forgot to mention...I'm a bit of a noob on this...

This is my first real linux box.

---

### Post by Jova on 2006-02-28
try to add more iwconfig stafs as 
wireless_rate auto
wireless_txpower 10

My acx111 nic is dead without it :|

---

### Post by Eyebolt on 2006-03-01
[QUOTE=Jova]try to add more iwconfig stafs as 
wireless_rate auto
wireless_txpower 10

My acx111 nic is dead without it :|[/QUOTE]

I added those to my interfaces...no such luck. It's wierd...I seem to get a connection by the time that it goes to update the clock using the internet, but by the time I get into my desktop, I no longer have an IP address, but iwconfig does show my essid and router address.

---

### Post by wclaps on 2006-03-05
I have been having the same problem.  Everything works fine after I restart wlan.  I usually do this in Gnome in network settings.  I'm using a broadcom based wireless card.  (Belkin - never again!)

---

### Post by Eyebolt on 2006-03-15
If I remember right...updating from the default installed ndiswrapper 1.1 to 1.10 worked for me.

---

