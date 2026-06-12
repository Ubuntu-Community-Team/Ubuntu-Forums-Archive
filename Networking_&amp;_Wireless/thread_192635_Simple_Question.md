---
title: "Simple Question"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by ness0216 on 2006-06-09
How do I configure my wireless on boot, my system just hangs for a while when it gets to "configuring network interfaces" basically i just want to run.
sudo iwconfig wlan0 essid "Name" enc open "Key"
sudo dhclient
Not sure how to make that happen.

---

### Post by nanotube on 2006-06-09
[QUOTE=ness0216]How do I configure my wireless on boot, my system just hangs for a while when it gets to "configuring network interfaces" basically i just want to run.
sudo iwconfig wlan0 essid "Name" enc open "Key"
sudo dhclient
Not sure how to make that happen.[/QUOTE]

well, just remove the line "auto wlan0" from the file /etc/network/interfaces
that will stop it from trying to configure it.
then, what you can do is put your commands into another startup script in /etc/init.d (without the sudo, because /etc/init.d stuff runs on bootup as root), and then enable that script by running
```
sudo update-rc.d nameofyourscript defaults 99
```
that will enable the script to run at default runlevels, after everything else.

try that. :)

---

