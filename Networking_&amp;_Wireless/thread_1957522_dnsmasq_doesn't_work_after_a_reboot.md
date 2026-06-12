---
title: "dnsmasq doesn't work after a reboot"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by jimerman on 2012-04-12
I installed and configured dnsmasq as both DNS and DHCP server.  Works great, nice and simple, and quick!

But here's the problem.  When I reboot, dns & dhcp don't respond.  When I log into the server, the service says it is not started (service dnsmasq status).  So I try to start, it says port 53 is already taken.  So I do "ps -e | grep dnsmasq" and sure enough there is a dnsmasq process running.  "service dnsmasq stop" doesn't work, so I kill the PID, and now I can start it with the "service" command.

Why is that?  I have to kill and restart the service every time I reboot.  I am trying to make a robust system that will come back up by itself.

---

