---
title: "eth0 down after pppoeconf"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by SilvioTO on 2006-04-11
hi, my problem is that after installed Ubuntu 5.10 (completely updated), and configured pppoe connection with pirelli ethernet modem, at reboot interface eth0 is "not active", down (before pppoe configuration at every reboot eth0 is ok). I must activate eth0 before the pon dsl-provider command for surf. At this point pon and poff command work. Another problem when, once activated eth0, try to configure session or network. From terminal have this results:

user@ubuntu:~$ gksudo network-admin
(network-admin:7065): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

user@ubuntu:~$ gksudo gdmsetup

(gdmsetup:7072): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

after this errors and two minutes the application start.

Another problem is the network icon on the gnome panel: on ppp0, if I clic on once, show error: SIOCGIFFLAGS - no such device.

help me please, thanks.
Silvio.

****************** interface file ***********************

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
iface eth0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

---

