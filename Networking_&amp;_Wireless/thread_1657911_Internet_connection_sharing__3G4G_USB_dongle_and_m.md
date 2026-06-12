---
title: "Internet connection sharing : 3G/4G USB dongle and my Netgear WGR614 wireless router"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by kennedyjch on 2011-01-01
I have internet access through 3G/4G USB dongle direct into my Ubuntu 10.04 box. Works great! Now I would like to share this connection out through my Netgear WGR614 wireless (and wired) router. Any clues? I've tried the simple (GUI) instructions using Network Manager, but just can't seem to get it right.

Previously, I had DSL and this plugged nicely into the WGR614 and internet and ethernet access was had by all. Now, I'm a bit confused on how to get the sharing (ethernet and wireless) between my Ubuntu box and the wired/wireless network while at the same time getting Internet access to all through the Ubuntu box.

TIA,

John

---

### Post by PatchesTheCaveman on 2011-01-01
Hi kennedyjch.  Happy New Year!

Follow these instructions:
[http://ubuntuforums.org/showpost.php?p=10305581&postcount=14](http://ubuntuforums.org/showpost.php?p=10305581&postcount=14)

---

### Post by kennedyjch on 2011-01-02
Thank you! Good start but still needed to tweak the second eth port (going to the router) as well as the router itself. For the former, I needed to give manual IP address (e.g., 192.168.1.2); DHCP was enabled in FireStarter using the same range (192.168.1.3 - 192.168.1.xx). The router itself in set to 192.168.1.1. For the latter, I needed to turn off DHCP on the router.

Works! Saves me time and $$$ should I consider buying one of the new 3G broadband + WiFi routers...

John

---

