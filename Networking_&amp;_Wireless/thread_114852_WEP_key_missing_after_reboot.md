---
title: "WEP key missing after reboot"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by oxygen_77 on 2006-01-09
Hey, I've gotten my wireless card setup and working, copied the WEP key to the networking control panel's WEP box, saved the setup, but everytime I reboot if I issue a "sudo iwlist ath0 key" command there are no keys listed.  I checked the /etc/network/interfaces file and the Key is correctly listed in there but for some reason it's not getting applied.  If I typed "sudo iwconfig ath0 key <wireless key>" then suddenly the wireless router can be found but I still have to issue a "dhclient ath0" to get my IP.  Is there some way I should arrange my /etc/network/interfaces file so that it will apply the key, discover the network and then issue the dhclient command?  

Oh, because the network is not discovered during boot, the boot sequence takes a really long time and of course fails name resolution.  This is how I know it's not connecting during boot.

---

### Post by nigerag on 2006-01-09
I have similar problem. My wireless card is recognized by the system properly and /etc/network/interfaces has all the settings listed. However, my laptop can not lease any IP adress. I did not have that problem with Ubuntu 5.04. I suspect that it has something to do with kernel 2.6.12. Is there any diagnostic procedure that will allow me to pin-point the problem?

---

### Post by oxygen_77 on 2006-01-10
[QUOTE=nigerag]I have similar problem. My wireless card is recognized by the system properly and /etc/network/interfaces has all the settings listed. However, my laptop can not lease any IP adress. I did not have that problem with Ubuntu 5.04. I suspect that it has something to do with kernel 2.6.12. Is there any diagnostic procedure that will allow me to pin-point the problem?[/QUOTE]I don't think this is a similar problem to mine...  I am able to connect just fine after I boot, but I have to do it manually.  My WEP Key is not being applied, but once I manually apply it then I can get an IP just fine.

I'm simply trying to figure out why my WEP key isn't being applied and what I should do to automate it.

---

