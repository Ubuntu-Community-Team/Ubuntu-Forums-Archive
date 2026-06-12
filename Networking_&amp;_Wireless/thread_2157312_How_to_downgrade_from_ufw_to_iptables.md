---
title: "How to downgrade from ufw to iptables?"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by shadowbox12 on 2013-06-24
I recently upgraded from 11.10 to 12.04 and I'm not happy at all with the changes to ufw.  There are so many chains and rules now - before routing - after routing - before logging - after logging I don't understand any of it and I just want to go back to command line iptables which makes more sense.  What is the easiest/best way to accomplish this?  When I checked my init.d I saw there is no startup script for iptables, only ufw, so I would need to get that from somewhere.  Is there some package I can install?

---

### Post by CharlesA on 2013-06-24
iptables do not have any rules after a reboot, so you would need to write a script to apply the rules you want to iptables after a reboot.

As far as using ufw, are you on a Desktop or Server install? gufw helps makes writing rules easier.

Otherwise just disable ufw: sudo ufw disable
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

