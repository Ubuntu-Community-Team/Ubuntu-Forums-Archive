---
title: "network connections problem"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by kristiansuhl on 2008-12-10
hello!

I have this strange problem in my ubuntu 8.10. To get online is easy, I just fill in the IP number and so on in the network connections settings panel, I get online and it all works - until I restart the computer! When computer is restarted I have to fill in the stuff again. Everything else works fine in the computer though, It remembers settings in other programs. 

This was not the case with the older version, it started happening with the new one. Very strange, any ideas?

Oh, and it also replaces my netmask with "24" too...

---

### Post by Iowan on 2008-12-11
/24 is the CIDR version of 255.255.255.0.  If that's a static network address, this [workaround]("http://ubuntuforums.org/showthread.php?t=974382") *might* help.

---

### Post by opus_az on 2008-12-11
> There seems to be a known bug with the Gnome Network Manager included with the Ubuntu 8.10 release that resets any static ip address settings that are set manually when the system is rebooted reverting back to a DHCP setup.

We saw this bug on two new stations this week. One we futzed with the GNM a bit and somehow got the static to stick. Who knows what we did. The other we edited the interface and resolv.conf files as mentioned in these links.

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

We didn't know about the bug or these links til after. Makes me want to go back and futz some more, but they're already deployed.

---

