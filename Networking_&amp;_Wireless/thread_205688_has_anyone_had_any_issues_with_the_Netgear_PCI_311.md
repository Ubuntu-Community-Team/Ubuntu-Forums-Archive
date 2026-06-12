---
title: "has anyone had any issues with the Netgear PCI 311T wireless nic and dapper drake ?"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by TOPPEL on 2006-06-28
has anyone had any issues with the Netgear PCI 311T wireless nic and dapper drake ?

i cannot connect with this one or the Linksys WMP54G despite having been told by someone in person it worked out of the box with Ubuntu.  i heard the same line on the forums regarding the Linksys wireless nic.  

thanks

:lol:

---

### Post by bigken on 2006-06-29
Hi try this for linksys 

[http://www.ubuntuforums.org/showthread.php?t=185174]("http://www.ubuntuforums.org/showthread.php?t=185174")

and this 1 for the netgear reply 3 

[http://www.ubuntuforums.org/showthread.php?t=202204]("http://www.ubuntuforums.org/showthread.php?t=202204")

both worked for me hope this helps ;)

---

### Post by TOPPEL on 2006-06-29
[QUOTE=bigken]Hi try this for linksys 

[http://www.ubuntuforums.org/showthread.php?t=185174]("http://www.ubuntuforums.org/showthread.php?t=185174")

and this 1 for the netgear reply 3 

[http://www.ubuntuforums.org/showthread.php?t=202204]("http://www.ubuntuforums.org/showthread.php?t=202204")

both worked for me hope this helps ;)[/QUOTE]

thank you

i did not read the netgear thread thoroughly as i read i only had to edit /etc/modules.d/config

here is my skinny:

unfortunately neither firmware worked.  btw i am assigning static ip addresses when trying to authenticate.  if i leave it as dhcp it has to login via SSID and hex key.  i never let it warm up though.  i did alot of tinkering and neither firmware seemed to work after ath0 activation and exiting the networking section.  

#-o

here is my /etc/network/interfaces with hex garbled

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1


iface ath0 inet static
wireless-essid MYSSID
wireless-key GARBLEDHEX
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

-=-

for dns servers i'm using the gateway of my router

-=-

here is my /etc/modprobe.d/config
cat /etc/modprobe.d/options
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options acx firmware_ver=1.2.1.30

i have a version 1 of the card.

could it be dns server as gateway is incorrect in Gnome networking?

also --

~$ cat /etc/resolv.conf
nameserver 192.168.1.1

works for eth0

lspci | grep Atheros
0000:00:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

