---
title: "Please Walk Me Through VPN Sharing"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by AlexEagar on 2009-06-15
***SOLUTION*** It turns out all I had to do was edit the network configuration for the secondary NIC that will be connected to a switch and then to my local devices. In NetworkManager, under 'IPv4 Settings' I changed Method: to 'Shared to other computers' and that's it. I haven't tried it with my switch yet, but I figure if it can give one device Internet, I'm sure it'll give multiple devices the Internet just fine.
----------
I have Ubuntu 9.04 i686 with two Ethernet connections. My ISP requires me to connect via VPN to access the Internet. My network cable is connected to my built-in NIC and I would like to share my Internet using my secondary NIC or the other way around if that would work better. I have found a [howto]("http://ubuntuforums.org/showthread.php?t=91370"), but I don't know how to adapt it precisely to my needs. Would someone please walk me through exactly how to configure this?

---

