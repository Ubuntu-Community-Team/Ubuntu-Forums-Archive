---
title: "none of networks mounted after booting"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by vogia-fr on 2006-03-01
Hi

I'm a Ubuntu 5.10 Breezy Badger newly installed

and I am none of networks mounted while boot is finished !

if I manualy activate 'wlan0' and 'eth0' : it is good
but 'lo' is'nt actived

this is my /etc/network/interfaces:

[COLOR="Purple"]
mapping hotplug
             script grep
             map wlan0

# the primary network interface
iface wlan0 inet static
address 192.168.xxx.yyy                # fixed address for adsl router modem 
netmask 255.255.255.0
gateway 192.168.xxx.1
metric 1
wireless-channel 9
wireless-essid ............
wireless-key ............
wireless-mode Managed
wireless-power off

auto wlan0

iface eth0 inet static
address 192.168.xxx.yyy               # fixed address for local sub-network
netmask 255.255.255.0
gateway 192.168.xxx.1
metric 1
metric 10

auto eth0[/COLOR]

---

