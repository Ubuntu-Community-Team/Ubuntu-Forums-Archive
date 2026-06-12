---
title: "Marvell 8056 - make settings permanent"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by ryanferreri on 2009-04-03
Hi all,

I have an onboard NIC that's a Marvell 88E8056. When I start up, it autonegotiates with my switch at 100 Mbps (yes I have CAT6, etc). I can force it to connect at 1000/full by issuing:

sudo ethtool -s eth0 speed 1000 duplex full autoneg on

...but every time I reboot it will autonegotiate at 100/full again. How can I make this setting permanent?

---

### Post by chili555 on 2009-04-04
Try this:```
sudo gedit /etc/rc.local
```Add your code, less the *sudo*, on its own line, just above *exit 0*, as follows:```
ethtool -s eth0 speed 1000 duplex full autoneg on
```Proofread, save and close gedit. Upon boot, your settings should be in place.

---

