---
title: "Ubuntu, DNS, DD-WRT."
date: 2012-02-16
forum: Networking &amp; Wireless
---

### Post by Roasted on 2012-02-16
Hi there. I have a Linksys E3000 with DD-WRT installed. One of the features I like about this setup is DD-WRT has DNS services, which is nice since I have some Samba shares floating around on my systems.

But I got to wondering, what if my lease expires and my IP changes on a specific computer? How long would it take DD-WRT to "refresh" its DNS tables and acknowledge the new IP of my system?

EDIT - I'm gathering now that DNS works off of DHCP, where when my computer requests an IP, it sends my host name. When I forced myself to have a static IP, I was doing so to ensure I would not get the same IP again so I could test to see if DNS was working properly by pinging my host name from another computer once my main desktop received a new IP... only to find out via static, things don't exactly work the same way, whereas with DHCP (mentioned above) part of the process of getting an IP is also exchanging the host name... hence why DNS seemed to work on DHCP yet when I put my desktop on static, it failed.

Does my explanation make sense? I think I get the jist of it. Speaking of which, is that to say that if my desktop ever grabs a NEW IP, it'll instantly update the host name on the router? (since that seems to be part of the IP assignment process?)

---

