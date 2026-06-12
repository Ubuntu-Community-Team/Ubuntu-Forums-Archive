---
title: "Multicast over GRE tunnel between Cisco and Ubuntu 11.10"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by thiagoas on 2012-01-08
Good afternoon,

I have a problem to carry forward the multicast tunnel gre I have between my internal network and the other end.

Unicast were tested with telnet the ips and ports to the internal network but multicast side B can not travel.

I tried with pimd, smcrouted, imgpproxy and still does not work.

Anyone have any idea to solve?

My firewall is cleared of all traffic to the internal network ips IGMP (224.0.0.0 / 4) and also for the IGMP protocol.

I applied the settings in sysctl.conf:

MC # Forward
net.ipv4.conf.all.mc_forwarding = 1
net.ipv4.conf.gre0.mc_forwarding = 1
net.ipv4.conf.eth0.mc_forwarding =
net.ipv4.conf.eth2.mc_forwarding = 1
net.ipv4.conf.eth3.mc_forwarding = 1
net.ipv4.conf.bovespa.mc_forwarding = 1
net.ipv4.conf.gre0.mc_forwarding = 1

# Forward
net.ipv4.ip_forward = 1



Can anyone help me?

If someone still have Skype and want to add me: s3ri4l is the user.

Thank you,


Thiago Anderson

---

### Post by thiagoas on 2012-01-11
Good morning all,

thanks for the help, I solved the problem as a routing software called XORP.

Thz.

:popcorn: :p

---

