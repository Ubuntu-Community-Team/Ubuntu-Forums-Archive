---
title: "IPv6 issue"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by prabhat0027 on 2011-07-21
I am not able use INTERNET in my ubuntu 11.04 which i have installed using USB  booting ,
 I am getting error "no IPv6 router present " on performing troubleshooting steps.
Although ubuntu shows that my computer is connected to Internet , also my bit torrent is working .
kindly suggest steps to recover this issue , i am using belkin usb adapter for connecting to Internet.

---

### Post by lemming465 on 2011-07-21
Do you have a DNS resolution problem, e.g. nothing configured in /etc/resolv.conf?  What happens if you try "dig www.google.com"?  Could we see the output from "ip address show; ip route show"?

Not having an ipv6 router, while not desirable, is in fact typical; most people are using ipv4 routing currently.

---

### Post by jmoorse on 2011-07-21
Does web browsing work for you?  If yes:

Don't worry about the message "No IPv6 router present".  If you want a technical blurb on why, here it is:

This is likely just your Ubuntu box (with IPv6 enabled) sending a router solicit message and not receiving a response.  Hence it assumes, due to lack of a response, that not IPv6 enabled routers are available as they would responsd with a router advertisement.  More info here: [http://www.cisco.com/web/about/ac123/ac147/archived_issues/ipj_7-2/ipv6_autoconfig.html](http://www.cisco.com/web/about/ac123/ac147/archived_issues/ipj_7-2/ipv6_autoconfig.html)

---

