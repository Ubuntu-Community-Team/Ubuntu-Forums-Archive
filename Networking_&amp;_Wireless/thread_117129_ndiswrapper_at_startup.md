---
title: "ndiswrapper at startup"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by Inarius03 on 2006-01-14
I have Ubuntu 5.10 with ndiswrapper running the bcmwl5 driver (Broadcom wireless).

Everything is working, but each time I reboot I have to:

iwconfig wlan0 key restricted

and then

dhclient wlan0

to get online each time.

I already put in 'ndiswrapper -m', but still doesn't work. I read something about putting ndiswrapper into the load-up modules, but I don't know how to do that.

EDIT: I put ndiswrapper in /etc/modules but still doing the same thing. Anyone?

---

### Post by wclaps on 2006-01-14
I have the same problem.  When I boot, Wlan0 is detected and set up but it has no ip address.  I have to disable it and then enable it to get it to take an IP address.  Then everything works really great!

---

### Post by healychan on 2006-01-14
First, ```
more /etc/network/interfaces
```and check that if you have a line looks like```
auto wlan0
```where wlan0 should be the name of your interface.

If you don't see that line, add it to /etc/network/interfaces file then.
This causes the system to configure the interface during startup

Backup your file!!

---

### Post by Inarius03 on 2006-01-15
Found out the problem.

I had the "s:" in front of my network key in the interfaces files, so it wouldn't take the network key, as it wasn't ASCII.

Working perfectly now, and thank you very much for alerting me to the prescence of that file (I'm a Linux noob)! :cool:

---

### Post by healychan on 2006-01-15
[QUOTE=Inarius03]Found out the problem.

I had the "s:" in front of my network key in the interfaces files, so it wouldn't take the network key, as it wasn't ASCII.

Working perfectly now, and thank you very much for alerting me to the prescence of that file (I'm a Linux noob)! :cool:[/QUOTE]
Enjoy your unwired box then:p

---

### Post by wclaps on 2006-01-17
I looked and it was there.  Still having problems.
Here is my configuration file:
[COLOR="Red"]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface wlan0 inet dhcp
wireless-essid linksys
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

auto wlan0[/COLOR]

Is the "auto wlan" in the right spot?

---

