---
title: "Wireless Tool To Manage Large Wifi Network."
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-12-30
At work we have a large wireless network that we're always changing and adding on to. As a result, it'd be nice if I would be able to tell the signal strength of each individual access point instead of just seeing one instance of the network's SSID.

WICD does this, showing me all of the access points, their signal strength, MAC address, etc. This is VERY nice. What's not nice is WICD can only hold a wifi connection for about 5 minutes before it will randomly drop me and re-connect again. 

So, WICD is out, and I'd like to continue using the default KNetworkManager since I have great luck with it. Is there any applications that can "scan" the network to see the individual access points and their signal strength? I'm running KDE if it matters, but I assume any Linux app would work fine. Any ideas?

---

### Post by Project PWNED on 2009-12-30
It's a command line application, but this will work better for you than some graphical interface program

> iwlist wlan0 scan

---

### Post by Roasted on 2009-12-30
Thanks. I'll give that a shot. But meanwhile are there any GUI tools for it? 

Does that command line tool you told me about also give back MAC addresses of each access point as well?

---

