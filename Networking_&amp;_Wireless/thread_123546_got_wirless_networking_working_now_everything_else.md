---
title: "got wirless networking working now everything else is so slow"
date: 2006-01-30
forum: Networking &amp; Wireless
---

### Post by mannu on 2006-01-30
Interesting,

I've managed to get wireless on the go and now going into editors like nautilus take for ever to load up. As well as genrally the system feels a lot slower

Stage 2 of my conversion to linux was to be able to print using my minolta QMS magicolor printer. So thoughts were to go to system, administration, printing and try from their. No joy. I get a command saying cannot find server for cups.

As a final issue when i do get wireless access I have to initiate initiate manually by going into sytem, administration and networks and activating r0 is it not poosible to automate this on boot up?

---

### Post by johannes on 2006-01-30
> 
I've managed to get wireless on the go and now going into editors like nautilus take for ever to load up. As well as genrally the system feels a lot slower
What kind of network devices do you use? And what drivers to get it working? Do you use encryption, WPA, WEP?

> Stage 2 of my conversion to linux was to be able to print using my minolta QMS magicolor printer. So thoughts were to go to system, administration, printing and try from their. No joy. I get a command saying cannot find server for cups.
I don't know how to be able to use it since I don't have one of those, but after a quick googleing i found [this]("http://linux.softpedia.com/get/Printing/foo2zjs-8802.shtml"). You might also be able to use [Turbo Print]("http://www.turboprint.de/english.html"). It's commercial though.

> As a final issue when i do get wireless access I have to initiate initiate manually by going into sytem, administration and networks and activating r0 is it not poosible to automate this on boot up?
You need to edit the file /etc/network/interfaces. Write in a terminal:
```
sudo gedit /etc/network/interfaces
```
and change it to fit your needs. Mine looks like this:
```
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

# The primary network interface
# iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid domherre

auto eth1
```
eth1 is my wireless card and eth0 is my cable one. This configuration activates my wireless on boot up and disables the other. I haven't gotten both to work at the same time but then I never use the other. You will need to change the names to fit your system, eth1 to r0 and eth0 to whatever.

The # character in the beginning of the lines means the stuff on that line will not be loaded. You can delete it instead, but I like to keep it there.

---

### Post by mannu on 2006-01-30
Thanks,

regarding your first requests I am using a belkin wireless g PCI card running on i think its a 2500 somehting chipset

I am using wep and this took me ages to get working my file looks likes this..

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map ra0


auto ra0

iface ra0 inet dhcp
wireless-essid *********
wireless-mode managed
wireless-key1 **********
wireless-defaultkey1
wireless-keymode restricted
wireless-enc on
wireless-channel 6
post-up iwconfig ra0 enc on

thanks,

paul

---

