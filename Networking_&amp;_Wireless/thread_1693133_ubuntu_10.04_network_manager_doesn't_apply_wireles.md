---
title: "ubuntu 10.04: network manager doesn't apply wireless configuration"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by splinux on 2011-02-22
Hello folks.
5 years and Ubuntu is (I am probably) still clueless in wireless networking. :KS :KS :KS :KS :KS

I am using ubuntu 10.04 with Gnome.

My wireless was working out of the box untill i must have had some network connectivity that made me decide to change.

the IP of wlan0 was set to 192.168.1.2 and I was accessing an AP configured without DHCP and with WPA2-PSK capability. This was allowing me to connect to a remote server with an interface configured in the same ip range (i.e. 192.168.1.1).

Now I changed the server and this MUST have a different IPv4. I could connect to it once I gave to my card an address in the same range (all is static and i masy say there was no IP configuration clash for sure).

I have an eth0 iface that has a public ip in the range 130.xxx.xxx.xxx. and that i use to connect to another network (obviously :) ).
the two interface worked perfectly togheter before and after i changed the server. Now the F***ng ubuntu decided it was time to stop working. It seems that ifconfig don't go along so much with the network-manager itself. Strange thing is i configured once with ifconfig and now someething happened.

So i starter setting Wifi config. from the network manager. The system try to connnect to the same SSID i supplied but with an Auto Configuration setting, never trying to use the one i made: more in detail i have Manual(static) IPv4, the AP MAC address, the SSID and I checked the box "connect automatically".
Didn't use the iwconfig tool as I cannot configure WPA2-PSK security with it, as most of you now. (so I consider it useless).
Wireless on Ubuntu is really pissing me off. :(

Can somebody help?
Thank You.

Splinux

---

