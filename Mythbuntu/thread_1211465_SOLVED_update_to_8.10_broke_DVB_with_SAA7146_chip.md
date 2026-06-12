---
title: "SOLVED: update to 8.10 broke DVB with SAA7146 chip"
date: 2009-07-12
forum: Mythbuntu
---

### Post by joho500 on 2009-07-12
I submit this post for others who encounter the same problem.

After updating to 8.10 my Technotrend Budget T-1500 card wasn't recognized anymore. After some searching around I found the answer on the site of Linuxtv.org: [http://www.linuxtv.org/wiki/index.php/Philips_SAA7146]("http://www.linuxtv.org/wiki/index.php/Philips_SAA7146"). I had to blacklist the module snd-aw2. You can do that in /etc/modprobe.d/blacklist.

Joost

---

