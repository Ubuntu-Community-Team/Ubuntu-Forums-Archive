---
title: "Network configuration creates problems at boot and not working."
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by Zardoz777 on 2013-07-05
I'm trying to set a statip IP address to in my  linux mint 14 system. After doing some changes my  /etc/network/interfaces reads this way:
--------------------------------------------------------------
auto lo
iface lo inet loopback

auto wlan0
allow-hotplug
iface wlan0 inet static
       address 192.168.1.66
       netmask 255.255.255.0
       getaway 192.168.1.1
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
---------------------------------------------------------------------

When  I booted after editing the file, the network does not function. Indeed,  the network controls on the right bottom of the desktop are not even  there. 
Also I wanted to set an static eth0 address to conect to my raspberry pi. So I have tried to add to the file:

------------------------------------------------------------------------------------------------------------
auto eth0
iface eth0 inet static
   address 192.168.1.66
   netmask 255.255.255.0
   gateway 192.168.1.1
------------------------------------------------------------------------------------------------------------
When  I do this the computer has problems to boot because says a drive with  an UUID which does not exist is not ready; "disk drive UUID=... is not  ready yet or not present".  Afer complaining it boots but network does  not work. I have read in the Ubuntu forum that people get this message  for other kind of reasons. Not for editing the /etc/networ/interfaces  file.

Anybody knows what is happening? I'm very novice with network configurations so probably I have messed up something.

Thanks!

---

