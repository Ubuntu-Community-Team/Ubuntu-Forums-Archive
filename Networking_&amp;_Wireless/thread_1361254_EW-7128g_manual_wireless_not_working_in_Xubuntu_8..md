---
title: "EW-7128g manual wireless not working in Xubuntu 8.04"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by thedukesd on 2009-12-21
The problem is simple I need to connect to the wireless network and use static ip (there is no dhcp in the network).

If I let enable roaming it connects to the wireless router but it don't get any ip (no dhcp server so I think it's acting right cause if I made a pc acting as a dhcp server it gets ip/gateway and of course everything is working).
If I try to use manual conection (everything is set right) it's just not working (the wireless router ip is 192.168.1.1, client ip is 192.168.1.2 subnetmask 255.255.255.0 gateway 192.168.1.1 corect essid and password, attempts to browse 192.168.1.1 (trying to acces the web interface of the router) fail, it's acting like there is no conections between the client and the wireless router). The ncryptions is set to  WPA2 (cause this is the encryptions of the wireless network), when I come back to the manual settings the encryptions is always changed to WPA. I think it's not connecting to the wireless router.

I'm using the NetworkManager. Xubuntu 8.04 is updated (when i used the dhcp server i updated Xubuntu hoping it will solve my problem but it didn't solved it).
There are 2 options I'm doing something wrong or NetworkManager is not connecting to the wireless router if I use manual configuration (maybe cause it's trying to use WPA and not WPA2 or maybe cause it's not even trying to connect to it).

When it comes to Linux I'm kinda noob :) .

---

### Post by thedukesd on 2009-12-22
There was no way to make the default Network Manager do what I needed or at least I was not able to find a way.

[Wicd]("http://wicd.sourceforge.net/") solved my problem.
This from the Wicd install guide didn't worked:

> wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

I dowload wicd.grg and imported the key.

Time to move to the other problems that I have to solve with xubuntu...

---

