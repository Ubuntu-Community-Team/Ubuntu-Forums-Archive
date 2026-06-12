---
title: "Quick question"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by Ryily on 2013-01-26
Hey guys, I have a quick question.
How do I setup a static IP for my Xbox using Ubuntu (12.04).
For those who are confused, my laptop is in my room and I run an ethernet cable from my Xbox to my laptop and I use 'Shared to other computers' on the IPv4 settings and use 'Ignore' on the IPv6 settings.
Currently I'm using 'automatic' on my Xbox so it grabs an IP from DHCP (I think that's correct?) BUT it makes my NAT type strict so I need to set a static IP so I can port forward, when I set a static IP on my Xbox it doesn't let me connect to XBL so I've figured I've got to do something on the system.

My network interfaces file:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.135
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

The only devices for networking I have are eth0 and wlan0 I think.

Thank you to anyone who can point me in the right direction.

---

