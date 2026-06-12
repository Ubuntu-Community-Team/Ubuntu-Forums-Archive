---
title: "Network Layout thru VPN"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by trileru808 on 2009-06-09
Hello guys. I have a network to build but can't figure out the settings.
I have 2 locations A and B witch are connected thru VPN MPLS. At location A I have the domain server and about 30 users, all in 192.168.2.0/24 subnet. The vpn router has 192.168.2.1 in location A and 192.168.1.1 in location B. In location B I also have the email server and a few other computers in 192.168.1.0/24 subnet. Also there is connected in B location a Linksys RV082 router witch is connected to the fiber link for internet. Linksys has 192.168.1.3 for LAN IP in location B. Now, I need all the computers from A and B to access the internet from the linksys router. The ones in A location should access internet from B location by VPN line. I also need that all computers in A and B to reach eachother.
Right now if a computer from B has linksys router as gateway it can surf the web, but it cannot be seen by any computer from A location. If it has as a gateway the vpn router (192.168.1.1) then it can see the computers in A location, but cannot surf the web anymore. I couldn't connect to the internet any computer from A location.
The VPN routers are Cisco 1803 and they belong to my internet provider, I cannot change anything there, only the Linksys router. If needed I could contact the ISP to make changes in Cisco routers.
I attached an image with the layout. Can you give me any advice please?
Thank you very much.

---

