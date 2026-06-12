---
title: "One PC, two networks :How?"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by Surabaya on 2009-04-02
Hello, 

In my office I use Ubuntu 8.10. 
We have two internet access: one through a Debian (on the Debian we have also all the files shared) and one through a wifi connection (not connected to the debian).
On my PC I have a usb wifi dongle and a network card. 

I would like to :

- Be connected to the Internet through my wifi dongle, using the Wifi modem
- Be connected to the Debian through the network card to browse the shared files, but I don't want to use the internet connection from the Debian.

This is my interface:

auto lo
iface lo inet loopback


#iface pan0 inet dhcp


auto wlan0
iface wlan0 inet dhcp
wireless-key c6774663dd
wireless-essid Speedy Milan

auto eth2
iface eth2 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1


I also added route add default gw 192.168.2.254 wlan0. 192.168.2.254 is the IP of the Wifi Router for Internet.

The problem is that when on my pc the wifi is on and ethernet cable is plugged, my Ubuntu don't use the Wifi but the internet from the Debian.

Any idea how to solve this problem?

Thanks you in adavnce for your help.

Surabaya

---

