---
title: "Can't seem to find answer"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by silameth on 2011-09-18
ok on my 8.04 desktop wireless works fine. on my 8.04 server it sees it in lshw but no logical name like wlan0..... is there some reason one finds it and the other does not?

it is atheros chipset on wifi card, but in my mind if Desktop sees and can use server should aswell.

---

### Post by pastalavista on 2011-09-18
Probably the driver module isn't loaded in the server kernel. Post the output of```
lsmod
``` for the server and the desktop.

---

