---
title: "cant get usb wireless to work at boot!!"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by ncdirtbag on 2006-05-10
I have a netgear wireless usb adapter.. ubuntu works fine with it..
but when I reboot, wlan0 has no ip address. this is easily resolved with
/etc/init.d/networking restart
and poof, wlan0 has ip address, interface works fine..
but when I reboot, wlan0 does NOT have ip address again..

I think its because the network scripties run BEFORE the hotplug scripties..
I tried moving 
/etc/rcS.d/S40networking to /etc/rcS.d/S50networking
so that it would be after 
/etc/rcS.d/S40hotplug and /etc/rcS.d/S41hotplug-net

but this doesnt seem to work.. 
WTF?

:evil: ](*,)

---

