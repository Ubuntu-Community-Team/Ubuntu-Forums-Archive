---
title: "intel 82579 Gigabit Lan"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by jd58 on 2012-05-06
This was working ok in 10.04 but is not in 12.04. My wireless is working ok but I am wanting to connect to my router via a homeplug and ethernet from the Ubuntu 12.04 PC.  
 
How can I check to see what the problem could be pleae?

---

### Post by Gyokuro on 2012-05-06
could you check whether the correct driver get loaded? Your chip should be supported by e1000e.ko module

lsmod | grep e1000e

---

