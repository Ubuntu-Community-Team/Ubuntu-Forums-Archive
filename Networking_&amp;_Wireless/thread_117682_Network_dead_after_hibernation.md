---
title: "Network dead after hibernation"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by Adrian on 2006-01-15
Hello, I have this rather annoying problem. When I resume from hibernation, everything seems to be alright until I try to connect to Internet. I can't ping my gateway ("connect: Network is unreachable") at 192.168.0.1, even though eth0 seems to be active (listed in ifconfig and marked as "active" in Network Monitor).

Trying to disable and reenable eth0 does not work.

I'm hibernating by doing a **echo -n "disk" > /sys/power/state**, and the very same thing works fine in SUSE. In both Breezy and Dapper, I get these problems. Any suggestions? I really like hibernating my machine.

And yes, there are NO wireless devices involved :)

---

### Post by jasmuz on 2006-01-15
Have you tried restarting the "networking" service?

sudo /etc/init.d/networking restart

---

### Post by Adrian on 2006-01-15
[QUOTE=jasmuz]Have you tried restarting the "networking" service?

sudo /etc/init.d/networking restart[/QUOTE]

Thanks for the suggestion. However, it didn't seem to work.

```
root@ubuntu:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:10:a4:ed:42:a4
Sending on   LPF/eth0/00:10:a4:ed:42:a4
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
ifup: interface lo already configured
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:10:a4:ed:42:a4
Sending on   LPF/eth0/00:10:a4:ed:42:a4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Error : Name or service not known
run-parts: /etc/network/if-up.d/ntpdate exited with return code 1

```

I'm still unable to ping my gateway afterwards.

---

### Post by Adrian on 2006-01-15
OK, I found a very ugly solution. Since I'm using a PCMCIA network card, I can "reactivate" the network by pulling it out, plugging it in again and do a **/etc/init.d/networking restart**.

This is not an optimal soultion, though. Does anyone know how to make Ubuntu recognize the network without me having to pull out the card every time I resume?

---

### Post by Adrian on 2006-01-15
OK, I solved the "hotplug" problem.

It turns out that hibernation was disabled in the /etc/default/acpi-support configuration file. When I enabled it, hibernation from the logout prompt started working properly. When using that instead of the command line solution mentioned above, my network dies BUT comes to life when doing a **/etc/init.d/networking restart**.

Nice.

---

### Post by Adrian on 2006-01-15
Solved.

Adding [B]/etc/init.d/networking restart[B] to the file /etc/acpi/resume.sh did the trick. Everything is working now. Isn't Linux fantastic? :)

Maybe I should file a bug report about this.

---

