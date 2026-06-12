---
title: "New Sprint Sierra 250U not staying connected"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by n.brenner on 2010-10-01
OK everybody.....I upgraded from a 595U aircard to the new Sprint

sierra 250U 3G/4G ....solved the connection issue by doing this...

1. In terminal..sudo gedit /etc/modules...

under lp, add the word: option

file>save>quit

2. sudo gedit /etc/rc.local

under: #By default.....

add: echo"1199 0301" >/sys/bus/usb-serial/drivers/option1/new_id

file>save>quit

It connected immediately and had no problems until update

from 2.6.32-24 to 2.6.32-25 (the last update) this is in lynx

it connects for 10 seconds then drops....if I come up in -24 then

everything is OK

what changed and why...my gedits are still there in both

---

