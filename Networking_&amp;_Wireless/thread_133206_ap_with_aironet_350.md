---
title: "ap with aironet 350"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by proffies on 2006-02-19
My setup : 

1 wired , 2 wireless network cards.

The wired connects to parobolic antenne trough wireless ap point,no problem there.
A atheros based wireless card is used to ssh or freenx to the box, no problem either.
The other wireless is a cisco aironet 350 card. 
First the card show up double eth1 and wif0. I always configured it double !
Does someone have an explaination for this ?
This card i like to use as an hotspot, the essid shows up but it is not possible to connect to it. I included the /etc/network/interfaces file.

Maybe somebody can help here , or knows where to find some more information on using wireless cards as hotspots in ubuntu. I don't seem yo find any.

many thanks,

Marc Michiels  

/etc/network/interfaces:

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface


iface eth0 inet static 
address 192.168.123.10 
netmask 255.255.255.0
gateway 192.168.123.254


auto eth0

iface ath0 inet static
address 192.168.123.11
netmask 255.255.255.0
gateway 192.168.123.254
wireless-essid netwerkje
wireless-keys:****


auto ath0




iface wifi0 inet static
address 10.10.0.1
network 10.10.0.0
netmask 255.255.255.0
broadcast 10.10.0.255
gateway 192.168.123.254
wireless-essid RadioNiel
wireless_mode Master

auto wifi0


iface eth1 inet static
address 10.10.0.1
network 10.10.0.0
netmask 255.255.255.0
broadcast 10.10.0.255
gateway 192.168.123.254
wireless-essid RadioNiel
wireless_mode Master


auto eth1

---

### Post by proffies on 2006-02-20
I tried to achieve the impossible:

airnet 350 only runs ad-hoc or managed not as Master.

I reversed the setup atheros card as Master(ap point) and aironet to ssh or freenx
works ok now

proffies

---

