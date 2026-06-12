---
title: "Resolving hostname on local network"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by MangledOne on 2008-12-18
I found the below post and Im having the same problem, the only way that works is to add the IP to the hosts file, but only works if you have the IP to begin with. I can connect to the net without any trouble, is there an update Im missing or something Im not doing?

[http://ubuntuforums.org/archive/index.php/t-445174.html](http://ubuntuforums.org/archive/index.php/t-445174.html)

---

### Post by jonobr on 2008-12-18
Hello

Couple of recommendations, 
could you change your machines to a static IP address? Or does your router, switch or whatever support assign DHCP address based on mac addresses?
What kind of switch/router are you using? there may be a simple method of doing this based on your router type

---

### Post by MangledOne on 2008-12-18
> **jonobr said:**
> Hello

Couple of recommendations, 
could you change your machines to a static IP address? Or does your router, switch or whatever support assign DHCP address based on mac addresses?
What kind of switch/router are you using? there may be a simple method of doing this based on your router type

Hi

First of all I have a Billion router which in turn is wired to a D-Link access point, the router is setup to use DHCP and distributes the IP address through itself and the access point, it looks like its based on mac address as I seem to get the same IP address as well as the router interface is still picking up PC names that havent been on the network for a while

---

### Post by Iowan on 2008-12-18
A couple more things to check... The thread you referenced mentioned Winbind and nsswitch.conf.  Apparently positioning of "winbind" in the nsswitch.conf line is critical.  **dmizer** mentioned the proper sequence in a couple of threads (don't have them now) and may have discussed them in [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To.

---

