---
title: "Ubuntu box in home network create dropped packets issues"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by javiern on 2013-06-09
Hello,
I have a weird behavior in my home netwwork (2 windows laptops, one ubuntu 13 netbook, and an iphone): when I connect my ubuntu netbook into the home network, other devices in the network start to get http timeouts when navigating internet, among several instabilities in the network (overall slowness, errors copying files across devices, etc.). It is almost impossible to even connect to the router admin web page due to constant http timeout errors.

a. unplugging the ubuntu netbook from the network, fixes the issue, plugging it again immediately brings it back.
b. this happens if I cannot the ubuntu netbook to the router through wifi or wired. same behavior.
c. on a seperate laptop I just do ping <router IP>. if the ubuntu netbook is unplugged I usually get ping results < 5 ms.   When I connect the ubuntu netbook, I start to see around 20-40% of pings that return a "Request timed out" -> evidence of the issue. weird as it sounds, the ping target is the router and I tested that from 2 different windows laptops. disconnecting the ubuntu netbook from the network fixes the issue.
d. I checked the ubuntu firewall, resetted the network cofigurations, there are no routing tables set up, nothing. it is just like it creates interference in the network.
 
any help appreciated. I navigated the forums and found no similar behavior.

thanks.
Javier

---

