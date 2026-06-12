---
title: "Network connect will not automatically connect"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by milocat on 2010-11-14
I am trying to set up Server version 10.10 on a new ASUS TS mini. Installation was pretty routine. However I am having a problem with the network interface. I have to manually type:
[PHP]sudo /etc/init.d/networking restart [/PHP]to get the network to connect. Once I do that everything is fine. On a warm reboot or cold restart, my networking will not restart until I manually enter the line above from the prompt.

I have tried both dynamic and static addressing.

It is as if the network is not being started automatically at start-up.

---

### Post by Iowan on 2010-11-14
Post contents of */etc/network/interfaces* - Hopefully there's an "auto" line for your interface (eth0?).

---

### Post by milocat on 2010-11-15
> **Iowan said:**
> Post contents of */etc/network/interfaces* - Hopefully there's an "auto" line for your interface (eth0?).

Yes, I have tried both static and dhcp.

[PHP]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet static
#       address 192.168.1.104
#       netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255
#       gateway 192.168.1.1
#       # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers 192.168.1.1



# The primary network interface
auto eth0
iface eth0 inet dhcp[/PHP]

---

### Post by milocat on 2010-11-15
I solved my problem!! This link [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)[/COLOR] pointed me in the right direction. I had a problem with "Wake on Lan" even though I am not dual booting. This server did have Windows 2003 Server on it at one point though.

---

