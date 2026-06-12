---
title: "No wired network. Out of ideas..."
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by primaxx on 2010-11-02
Hello forum, I am totally lost now, and hope that someone else might see the solution to my problem.

The System is Ubuntu 10.10 server.

This started after I installed OpenVPN and bridge-utils.
After everything was configured properly I got it all working, and the system ran smooth. But now, after a reboot, it is totally impossible for me to get the server connected to any net at all.
[LIST]
[*]Initially the problem was related to that it could not find **br0**, so I uninstalled both OpenVPN and bridge-utils.
[*]That didn't help, so I reset the /etc/network/interfaces to default.
[*]Now, when I restart the network, it reports it gets no response from the dhcp-server.
[*]I know the dhcp-server works, and I know the network-cable is ok.
[/LIST]

netstat -nr gives me an empty ip-table.
ifconfig shows that eth0 has an ip6-address, but no ip4.

I have tried both with my router and 8.8.8.8 as dns-server in resolv.conf.

Please help me someone, I have bee struggling with this for days now... :(

---

### Post by primaxx on 2010-11-03
*Bump* Still out of ideas and desperately need some help...

---

