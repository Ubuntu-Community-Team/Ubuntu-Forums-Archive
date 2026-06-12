---
title: "Opening ports to solve VE_FMS_CONNECT_FAILED error"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2012-12-24
I'm running Kubuntu 12.10, and I've been having a persistent but apparently unusual problem: when I try to view Flash videos over the Net, I get the error **VE_FMS_CONNECT_FAILED**.  Other videos such as YouTube are OK; in fact, on the NYTimes site, there are videos with preceding commercials where I can view the commercial but not the content!

I found this explanation of the error in the BrightCove forum:
> This is the result of the Flash Media Server (FMS) being unable to establish a connection over port 1935; 443; and 80 leading to a connection timeout.

However, **ufw** tells me that the firewall is inactive and **iptables** has no entries. I've not done anything to configure either the firewall or the ports.  I get this both with Chrome and Firefox, so it seems to be unrelated to the browser.

Assuming the BrightCove explanation is correct, is there anything I can do about it?

---

