---
title: "4th attempt at sending this:Which router shjould i get"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2011-01-20
This is my 4th attempt at sending this same message. I just tried sending this message as normal but i kept getting proxy error from the forum end. Sorry to post same message 4 times.I need to set up a network at home. The set up i want is as follows:
```
|LAN|----|switch|----|linux firewall|-----|switch|------|ADSL/border router|

```
The problem at the moment is that the Linux firewall has to have it's NICs on different subnets( external(ia dhcp from border router on 192.168.1.*) and it's internal on 192.168.2.*). I can, with the current border router, change the subnetmask to 255.255.0.0 so that it doesn't "mind" dealing with addresses on the two different subnets. However i can't add a route to the internal LAN(192.168.2.*).So the border router only knows that the linux firewall is reached at 192.168.1.*. And there's no way, on this border router, to add a route to 192.168.2.*. So i can't ping the border router from my ubuntu hosts on the LAN. I can ping the linux firewall's internal and external interfaces from the ubuntu hosts on the LAN. But i can't ping the border router from the LAN because it doesn't know how to get to 192.168.2.*.
I need to replace the border router, which is just a home router, with a machine that has all the usual capabilities of a home router/ADSL box AND the capability to add routes to other subnets. IIt needs firewalling capabilities because plugged into the switch(coming out of the ADSL box), in the diagram, are 2 Ubuntu servers. It would also be good if it could do things like changing the subnet mask. As flexible as possible.I'm willing to spend a fair bit i.e less than 200 pounds. The other thing is it's got to be available in the U.K. Off the top of your heads is there any router that you could recommend that is good for a fully UNIX network involving different subnets that could replace a home router.
Or do i need a router that you can install a special Linux on? And if so are there any recommended?.
Thank you so much for your time and any replies. Fare ye well.

---

