---
title: "Max no. of IP addresses"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by tornadof3 on 2009-04-11
I am going to have to use a wireless router to manage an internet connection & DHCP etc on a small network and then use wired ethernet to connect the file server and another wired port to connect the switch.

My question is, on most wireless routers, will it issue more than 4 IP addresses (it has 4 wired ports), i.e. will clients connected via the switch (about 10) all be able to get IPs?

---

### Post by chili555 on 2009-04-11
Many consumer routers have a setting in their administration pages to allow up to a set number of IP addresses. My Linksys WRT54G is set at the factory at 50. Is that enough? I believe you could increase this to 253, if needed. Usually, the setting is used to limit the number of addresses allowed by DHCP; that is, to just enough for your network and no more. It puts a bump in the road, but not a brick wall, to drive-by hackers and pesky kids next door.

---

### Post by capscrew on 2009-04-11
> **tornadof3 said:**
> I am going to have to use a wireless router to manage an internet connection & DHCP etc on a small network and then use wired ethernet to connect the file server and another wired port to connect the switch.

My question is, on most wireless routers, will it issue more than 4 IP addresses (it has 4 wired ports), i.e. will clients connected via the switch (about 10) all be able to get IPs? 

The 4 wired ports have nothing to do with how many IP addresses the router will issue.  The router is capable of issuing all the IP addresses in the subnet you setup.  If this is a 24 bit subnet then it can have 254 addresses (.0 = network and .255 = broadcast).

chili555 is correct in that the dhcp component of the router usually is setup for 50 ip addresses.  You can change that to what ever you want.  I reduced mine to 10 addresses.  I also have static IP addresses in the network also.  You can mix static and dynamic addressing.

The 4 wired ports are actually a built in switch.  If you connect another switch to the switch you will add more wired connections.

---

### Post by tornadof3 on 2009-04-11
That's great, thanks for your quick replies guys.

---

