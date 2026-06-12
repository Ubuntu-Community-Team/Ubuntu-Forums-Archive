---
title: "Setting up a wireless bridge for Xbox"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by North101 on 2011-01-07
Hi,

I have a HTPC running a minimal version of Ubuntu (without a desktop GUI) and, so that I don't need to buy the wireless adaptor for the Xbox 360, I was hoping to setup a bridge between my HTPC's Ethernet and Wireless connections so that I can share my Internet connection using an Ethernet cable.

Basically something like this:
[**360**]-<*Ethernet*>-[**HTPC**]-<*Wireless*>-[**Router**]

My /etc/network/interfaces file looks like this:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


I have bridge-utils installed and I've tried a few methods I've found online using it, but no luck.

Thanks for any help,
North101

---

