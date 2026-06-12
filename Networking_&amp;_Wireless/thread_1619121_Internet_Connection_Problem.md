---
title: "Internet Connection Problem"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by mantalope on 2010-11-11
I have an Ubuntu 10.10 (64 bit on a Dell PowerEdge T310) that cannot connect to the Internet. The network interfaces work fine because I can connect to our local network and to the firewall appliance. The network is controlled via DHCP. I have another Ubuntu 10.10 machine that connects to the internet without any issues, so I don't believe that it is a firewall issue. Via networking tools, I am able to perform a lookup, so DNS appears to be working. When I perform a trace route, it makes it to my firewall and then returns "no reply" from there. In firefox, I time out on "connecting to ..." I also fail on any apt-get update calls.
 
I've disabled ipv6 in Firefox with no effect. Ifconfig results and gateway route is all correct.
 
Any ideas where to look next?

---

### Post by mantalope on 2010-11-14
I gave up troubleshooting and did a complete reinstall of Ubuntu 10.10. I did an apt-get update/upgrade without any problems. Then I installed gnome (apt-get install ubuntu-desktop) and now I cannot connect to the Internet. I can successfully perform an nslookup command, so it does not appear to be a DNS issue.

Any ideas of where to look?

---

