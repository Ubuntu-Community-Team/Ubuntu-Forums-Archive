---
title: "armada m700 8.04/8.10 ethernet issue"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by babygenius55 on 2009-09-12
My main question is how do I assign an ipv4 addr to my onboard ethernet card when Network Manager wont?

I have a compaq armada m700: intel ethernet pro 100
 
After reading 15 and attempting about 8 fixes, my problem seems to be this:  There is no ipv4 address assigned to my Ethernet card. ipv6 doesn't seem to work, the card tests out fine, but is not able to reach the router via wired connection.  I have no wireless connection.  I've edited just about every file I can think of to no avail.  the settings in the nm keep getting reset upon rebooting.  there is no option to unlock nm, but I've tried editing the settings in nm by opening with sudo.  I don't know how to get the nm (network manager) to assign an ipv4 addr to my card. there are people out there with very similar situations, but following instructions in launchpad and here, and other various places just doesn't work.  My install didn't have that *.conf file that shares it's name with the folder...I know I'm not being very descriptive, but not near my laptop right now.  ifconfig (when no settings are unchanged) shows an ipv6 addr, but no ipv4.  I've tried manually putting in 208.67.222.222, 208.67.222.220 for DNS, but that doesn't work.

---

### Post by babygenius55 on 2009-10-10
bump

---

