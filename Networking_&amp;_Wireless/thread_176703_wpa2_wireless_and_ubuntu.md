---
title: "wpa2 wireless and ubuntu"
date: 2006-05-15
forum: Networking &amp; Wireless
---

### Post by ivansv on 2006-05-15
installed dapper6 yesterday but that wpasupplicant is a pain in the butt.
i hope linux gets with the program in this area, microsoft is way ahead with wpa encryption. setting up my wife's xp was a breeze with wpa and now i'll wait until the final release of dapper in the hope they get it straight by then.
what are you'alls experience with wpa? anybody know a linux distro thats got a good wpa setup? thanks for your comments.

---

### Post by oscar on 2006-05-15
For me wpa wireless works (almost) perfectly, sometimes I cannot connect or lose my connection but I'm not sure if that is ubuntu or my router. Make sure you have network-manager-gnome installed and mn-applet is in your startup programs (I can't remember if you have to do this or if the package does it). You should get an icon in your notification area that you can manage your network connections from. The main bad thing about network manager is that every time you want to connect you have to enter your password (not your wpa key)
Wireless in dapper is alot easier than it was in breezy (I have found).

---

### Post by ivansv on 2006-05-15
thanks Oscar for your response. never tried network manager. the reason you're having luck may be your wireless hardware. i noticed when working to get wpa working over the weekend that in /lib/firmware some cards are already supported and their drivers are already there, not so mine a linksys wpc54g withe broadcom chipset. i had to download the bcm43xx driver, easy enough, and wxtract it with the bcm43xx-fwcutter and then had to work with the wpa_supplicant- a real pain- after 6hrs. of trying finally packed it in. in other words your card may be supported out of the box, mine is not, thats why i have to go thru these machinations to no avail.
don't get me wrong i am not bitter and cannot expect ubuntu to provide out of the box support for every wireless card out there. its just a shame ubuntu is a fine distro.

---

