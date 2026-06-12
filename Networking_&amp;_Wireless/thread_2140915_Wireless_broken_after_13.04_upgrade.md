---
title: "Wireless broken after 13.04 upgrade"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by glendavee on 2013-05-01
I have just upgraded to 13.04 (64bit) from 12.10. I had been using ndiswrapper-1.58cr1 for my wireless connection, but I can't get this to install in 13.04.
ndiswrapper -l shows :
[COLOR="#FF0000"]david@Neewdesktop:~$ ndiswrapper -l
bcmn43xx64 : driver installed
	device (0846:9020) present[/COLOR]
but 
[COLOR="#FF0000"]david@Neewdesktop:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.[/COLOR]
ndiswrapper version is
[COLOR="#FF0000"]david@Neewdesktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/ndiswrapper.ko
version:        1.58
vermagic:       3.5.0-27-generic SMP mod_unload modversions [/COLOR]

rfkill shows nothing is blocked.

Grateful for any suggestions

---

