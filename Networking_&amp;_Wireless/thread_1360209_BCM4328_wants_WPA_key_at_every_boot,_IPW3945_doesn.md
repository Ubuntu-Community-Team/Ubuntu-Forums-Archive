---
title: "BCM4328 wants WPA key at every boot, IPW3945 doesn't"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by amp_man on 2009-12-20
This is really odd. I've just finished setting up Ubuntu 9.10 x86_64 on my Dell XPS M1530, which came originally with an Intel 3945 card, and then I added a Broadcom BCM4328 for wireless-N and OSX capability (I don't have OSX anymore, but the wireless N comes in handy). When I log in, the Intel card finds my network, remembers the key, and connects. The broadcom find the network, tries to connect, and asks for my key. Any ideas? This is really annoying.

---

### Post by hugmenot on 2009-12-20
Does it work when you give it the key? I mean, is your problem just NetworkManager  forgetting the key?

---

### Post by hugmenot on 2009-12-20
BTW, I just remembered. As far as I know the N-PHY Broadcom cards don&#8217;t work yet.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

and

[http://markmail.org/message/csso75skwekm26ir](http://markmail.org/message/csso75skwekm26ir)

Or does it work meanwhile?

---

