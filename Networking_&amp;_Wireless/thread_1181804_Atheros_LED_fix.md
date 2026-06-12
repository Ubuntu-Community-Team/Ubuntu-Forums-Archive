---
title: "Atheros LED fix"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by xenosaga456 on 2009-06-08
to turn on the activity LED on a Atheros 5007 with the following commands: and u should use SUDO or assume the root in ur linux distro and this should work the same in kunbuntu

sysctl -w dev.wifi0.ledpin=3

sysctl -w dev.wifi0.softled=1

 To make this configuration permanent, we have to modify /etc/sysctl.conf and add this line at the bottom of it:

sudo gedit /etc/sysctl.conf



dev.wifi0.ledpin=3
dev.wifi0.softled=1


and ding ur done i hope this worked for u

---

