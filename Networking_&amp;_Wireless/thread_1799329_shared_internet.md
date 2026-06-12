---
title: "shared internet"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by lister king of smeg on 2011-07-07
I have a Ubuntu 10.04 laptop that gets its Internet connection via WIFI using WICD as network manager, and Windows XP desktop with no Internet connection. What I want to do is share my Internet connection from my laptop with my desktop via a Ethernet cable. But i have no idea what to do. How do i go about doing this?

---

### Post by flash63 on 2011-07-08
Hello,
use the connection skripts (post-up/pre-down).

You find the How-To here (German uu-forum), but all terminal-commands are english. 
[http://wiki.ubuntuusers.de/Internetverbindungsfreigabe#ICS-mit-Wicd](http://wiki.ubuntuusers.de/Internetverbindungsfreigabe#ICS-mit-Wicd)

Or translate it if necessary.
[http://translate.google.com/translate?hl=de&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FInternetverbindungsfreigabe%23ICS-mit-Wicd](http://translate.google.com/translate?hl=de&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FInternetverbindungsfreigabe%23ICS-mit-Wicd)

Attention! The translation program is changing the syntax of the scripts and commands!

Perhaps it will also need a crossed LAN-cable to connect.

See [http://translate.googleusercontent.com/translate_c?hl=de&rurl=translate.google.com&sl=de&tl=en&u=http://wiki.ubuntuusers.de/PC-Direktverbindung_per_Netzwerk-Kabel&usg=ALkJrhgaKf57ZkmflI7Wlo6lwMIqkqfZCg](http://translate.googleusercontent.com/translate_c?hl=de&rurl=translate.google.com&sl=de&tl=en&u=http://wiki.ubuntuusers.de/PC-Direktverbindung_per_Netzwerk-Kabel&usg=ALkJrhgaKf57ZkmflI7Wlo6lwMIqkqfZCg)
and [http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by lister king of smeg on 2011-07-09
thank you i will try it.

---

### Post by flash63 on 2011-07-09
Pay attention to the interface names for LAN and Wifi (eth0/wlan0) in the scripts that need to be amended as appropriate
```
ifconfig -a
```
The guidance works well here.

---

