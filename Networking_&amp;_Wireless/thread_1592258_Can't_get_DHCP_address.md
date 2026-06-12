---
title: "Can't get DHCP address"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by LINYbob on 2010-10-10
I have installed 10.10 on a new hard drive and booted up. I am using a Belkin USB wireless to access the router. If I plug in my Windows drive on this machine it works fine, of course.

Ubuntu does not. Viewing the /var/log/syslog, I can see that I am able to connect to the router, however it eventually fails with:

DHCP transaction took too long, stopping it.

If I do:

sudo dhclient wlan0 it fails the same way.

Any ideas? This is a totally clean installation, just trying to get it going for the first time.  I have had no luck finding anything via Google.



Like I said, with the exact same hardware, but with Windows, it all works fine. So its not like the router has some MAC exclusion or something (it doesn't - I checked). I have no problems getting a DHCP address except under this Ubuntu. Also I can see that I can authenticate to the router so it looks like all the drivers, etc. are working.


Also - what is the deal with having to enter the password constantly? It is so annoying. I am the only one on the system and I have to enter it to log on, to enter any command, over and over again. Very annoying.

---

