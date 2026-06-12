---
title: "VPN on eth0 with Linksys 4200"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by jardineworks on 2012-08-23
Hey guys,

I just don't know enough about this stuff to figure it out on my own so I am pleasing with the community.

I have a Witopia account that I use to VPN into the US to access restricted sites. I also use it to test restrictions my clients have (requiring visitors to only come from Canada). When I use my wireless card (wlan0) it works flawlessly. When I switch over to my eth0 card it fails. I did some research and there appears to be some issue in how Linksys does the port forwarding or something -- they're not following the mDNS spec or something.

I am using the network manager where I have configured the VPN connection. When I try to connect I tail the /var/log/syslog and I see this --

[B]avahi-daemon[1028]: Received response from host 192.168.1.1 with invalid source port 32768 on interface 'eth0.0'
[/B]
I have read countless pages but have not yet seen anything that suggests how to fix it.

Can anyone in the community help?

---

