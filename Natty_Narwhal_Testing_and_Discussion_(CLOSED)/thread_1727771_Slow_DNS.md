---
title: "Slow DNS"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Visceral Monkey on 2011-04-12
Arrg. For whatever reason Natty is SLOW when resolving DNS, like insanely slow. Does anyone have a fix for this? I seem to remember Ubuntu being plagued with this problem in previous releases as well.

Edit: After trying several things, including turning off IpV6, changing the nameservers to use the google ones at 4.4.4.4 and 8.8.8.8 seems to have done the trick. Also, I had to "lock" the /etc/resolv.conf file I did the edits to with "sudo chattr +i /etc/resolv.conf" because rebooting would reset the edits.

---

### Post by Visceral Monkey on 2011-04-13
See above.

---

