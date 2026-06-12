---
title: "DHCP Problem with Router in Bridged Mode"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by javacookies on 2012-08-09
Good Day to everyone out there willing to help a helpless like me :D
I'm having a problem with my network. I have two routers - 1 given by my ISP and 1 for my wireless network. The ISP router connects to the internet through dynamic IP. I connected it to my router to be able to use it on multiple devices. My router is in bridged mode.

Now here's my problem, my desktop running 11.04 can't connect to my router. It can't get an IP from the DHCP server. Although when I configure it manually and says it's connected, there's still no internet and I can't even go the router's configuration page. BTW, to have a picture of my network---- ISP router has the DSL line and it is connected to my wireless router and my desktop connects to my router. I tried directly connecting my desktop to the ISP router and boom! it worked and I'm posting this now. 

Sorry for the long post I just want to share everything that might help solving my problem. Thanks for any help I get :)

---

### Post by Kalanac on 2012-08-09
Hi there!  I've recently been having a play about with similar things, not exactly the same, but should be relatively similar.

Here is your topography from what you described:

Desktop <---> Wireless Router <-B-> Wired Router <---> Internet

(B = Bridge)

OK, stuff to check:

Is your wireless routers DHCP turned on and able to offer IPs?  Double check MAC filtering and security settings to make sure there are no possible connection issues between your desktop and the router.

Are you using separate subnet masks for the two routers?  Your wired router is considered your "primary router" so get its DHCP to assign IPs in the 192.168.0.x or 192.168.1.x range.  Your wireless router is a client router so get it dish out 192.168.2.x IPs.  (This might only be relevant to client router set ups rather than bridges)

Have you tried setting your wireless router to client mode?

---

### Post by javacookies on 2012-08-09
The wired router is the one with DHCP server here's it's config

IP Address	 192.168.1.1
LAN Subnet Mask	 255.255.255.0

Config of my Wireless Router

IP Address:	192.168.1.2
Subnet Mask:	255.255.255.0
Default Gateway: 192.168.1.254

BTW, my network works on Windows and only in Bridge mode. And if it's not clear in my post, all connections are wired.

Anyway thanks for the reply :)

---

