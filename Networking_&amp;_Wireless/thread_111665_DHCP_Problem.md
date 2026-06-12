---
title: "DHCP Problem"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by jon_z on 2006-01-02
Hello, I'm using a Linksys WMP54GS wireless ethernet card.  I have installed the windows driver using ndiswrapper.  I have the card setup properly for my network.  The problem is when I goto enable the wlan0 in System Settings -> Network Connections  it enables for a second, then goes back to disabled.  When the computer starts the network card does not.  The module for the card is running.  when i type 
$sudo dhclient wlan0  
I get internet connection  here is the feedback from the command. (Running this after already running it once.. thats why the pid is running)
$ sudo dhclient wlan0
Password:
There is already a pid file /var/run/dhclient.pid with pid 8086
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:66:f4:57:6a
Sending on   LPF/wlan0/00:0f:66:f4:57:6a
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 40425 seconds.

Any knowledge on how to get my connectivity when my computer starts would be greatly appreciated. Thank you.

---

### Post by Zelut on 2006-01-02
are you saying that the card works but it doesn't auto-retrieve the DHCP at boot?  does your /etc/networking/interfaces file have an entry for wlan0?  If not you can manually add one or try this (if you haven't...):

sudo ndiswrapper -m (adds it to the modules to load at boot)

---

### Post by jon_z on 2006-01-02
i have done  sudo ndiswrapper -m    . and yes, /etc/networking/interfaces has the entry for wlan0 it just doesnt get the dhcp information itself.

---

### Post by Lambert on 2006-01-02
Post the output of your interface file (xxx our all personal data)

Is this a pcmcia card on a laptop?

---

### Post by jon_z on 2006-01-02
this is a PCI card in a dell desktop..

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid   linksys
wireless_mode    managed
ndiswrapper -m


iface eth0 inet 

auto wlan0

the auto DHCP doesnt get the correct information, when i boot the computer, i open up a console and type do the following.

eric@Doom:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:66:f4:57:6a
Sending on   LPF/wlan0/00:0f:66:f4:57:6a
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 37753 seconds.
eric@Doom:~$

---

### Post by Lambert on 2006-01-03
remove the line that starts with name and the ndiswrapper -m line

ndiswrapper -m line only needs to be run once. What that command does is add ndiswrapper to the /etc/modprobe file so it loads the module at. you can check that file to make sure it says ndiswrapper.

also remove the second auto wlan0 stanza.

---

### Post by jon_z on 2006-01-03
no go, is there a way to create a script to run that command at boot?

---

### Post by jon_z on 2006-01-04
bump

---

### Post by jon_z on 2006-01-04
bump  * bump*

---

### Post by jon_z on 2006-01-05
bump again.

---

