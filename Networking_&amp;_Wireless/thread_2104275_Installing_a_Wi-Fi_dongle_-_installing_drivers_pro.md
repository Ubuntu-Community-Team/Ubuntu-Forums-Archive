---
title: "Installing a Wi-Fi dongle - installing drivers problems"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by Gamer Boy on 2013-01-12
I'm a total beginner using Ubuntu12.4.1


 I've purchased a wi-fi dongle that I want to install it. There are some drivers on a CD that was supplied with it, but looking around launchpad, I've also found links to zip-files of drivers for the dongle I use.


What I don't know is how you open these zip files and install the drivers.


I also don't know if I've done anything damaging in my try-anything previous attempts to unzip and install them.


My PC can clearly *see* the dongle as it allows me to see the wifi network in my home - but every attempt to log on to it fails.


Running lsb_release -a; uname -a; lsusb in Terminal gives me this output:


martin@martin:~$ lsb_release -a; uname -a; lsusb
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
Linux martin 3.2.0-35-
generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 i686 i686 i386 GNU/Linux
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
martin@martin:~$


Any tips / comments welcome?

---

### Post by squakie on 2013-01-12
Follow this thread:

[http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/](http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/)

---

### Post by ahallubuntu on 2013-01-12
Like I suggested in your other thread:

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

There's a chance the driver on CD is outdated and you should download the latest from Realtek, anyway.

---

### Post by squakie on 2013-01-12
Again, that's what the thread I posted does.  Just because it says mdimx doesn't mean it's wrong - it's the same chipset.

---

### Post by Gamer Boy on 2013-01-12
Thank you! All solved now.:D

---

### Post by squakie on 2013-01-12
don't know if I helped or not - if so, you're welcome, if not, sorry! ;)

---

