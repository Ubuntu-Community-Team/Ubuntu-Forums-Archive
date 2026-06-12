---
title: "Intrepid Slow Internet &quot;Looking Up...&quot;"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by jason50146 on 2009-01-18
All-

I wanted to post this to try and help others that may have been having the same problems.

After installing intrepid, I noticed a substantial slowdown in performance of web browsing.  At the time, I was dual booting with Vista.  IE was loading pages a lot faster than Intrepid, so I knew it was not my hardware.  In addition, I did not recall having this problem with Hardy.  I tried a number of things after several searches.

After a lot of time, I determined my problem was not related to:
IPv6
Firefox "Attack site" database
Firefox proxy settings
MTU setting

I even tried Opera with no luck.  It, too, was opening pages at a snail's pace.

Eventually, I made my way to "connection information" in the network manager and saw that my primary DNS was set to my router DNS. This is not correct for my setup.  I'm using my ISP's DNS.  Thus, programs accessing the internet were going to my router first, waiting for a timeout, and then going out to my ISP DNS.  

With this information in hand, I was able to find the archived post below:

[_Set Primary DNS_]("http://ubuntuforums.org/showthread.php?t=337553")

Following the information in this post got Intrepid running great on the internet.  Lookups fly by now, which improved page loading speed considerably.

Hope this helps someone out there!

-Jason

---

### Post by Macchi on 2009-01-18
Many routers have a DNS cache, a function that can speed up local response times. But that function has to be explicitly activated sometimes and you must have the correct DNS settings on the router and DHCP.

Eventually these details main be overseen while setting static IP adresses (public and private IP adresses). I have also seen problems caused by providers that without notice may change the address for their DNS servers or have them down temporarily for maintenance.

---

### Post by esharf on 2009-01-18
Another way of doing this if you're on the desktop version is to go System > Administration > Network, unlock the Network Settings, go to the DNS tab, and delete your router's DNS entry.

Applied on 8.04 desktop.

Eric

---

