---
title: "ath0 is missing"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by c-2501 on 2006-03-08
the title says it all really, untill earlier today i was running my wireless connection (through a Netgear WG311T) perfectly well, i reboot and all of a sudden the device seems to have dissapeared.  i cant see it in either my network settings or in the device manager.

the only change i have made to the system today is to upgrade the Nvidia graphics drivers, following the guide on these forums.

the wireless card itself is functioning perfectly (i am currently writing this wile connected to the same network through windows)

so whats gone wrong? and how do i fix it.

if you need any more info just ask, please help me fix this :confused:

---

### Post by spd106 on 2006-03-08
Did you remove the linux-restricted-modules package that contains the atheros driver?
If so you'll have to either remove your new graphics driver and re-install that package or you could compile the latest madwifi driver. There's a howto around somewhere.

---

### Post by c-2501 on 2006-03-09
yup i found the howto, tried to follow it but i have a few problems

1) i cant connect to the internet and do apt-get without my wireless
2) downloading the required files before hand didnt work (for some reason the make oppertion faild disasterously, why i expected it to be that easy i'll never know)
3) the URL [http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz](http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz) is now 404 the repository has been moved 

is there anyway to install the drivers without screwing up the madwifi modules
or
is there a way to successfully restore the modules after the drivers have been updated.

***edit*** well nvm i got it fixed on my own

---

