---
title: "Sony Vaio 802.11N no faster than 54Mbit"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by bthoward on 2010-10-18
Ok so I'm having trouble with 802.11n as of late in Ubuntu.  I know my wife's computer used to connect faster but it seems to not be able to go over 54 Mbit in 10.10 any more either.

Laptop is a stock Sony Vaio VPCZ12CGX/x which has an Intel Advanced-N 6200 card.

LSPCI output:
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

I can connect to the 2.4Ghz channel or the 5Ghz channel on my wap both are capable of up to 300Mps as per its configuration but neither go over 54Mbit.  Both do about 160Mbit from this same location in Windows.  Moving closer makes no difference.  

Any thoughts would be greatly appreciated.

---

### Post by bthoward on 2010-10-22
Found that this is related to a bug in the iwlagn driver and all mavrick users with that driver are disabled from using 802.11n until it gets sorted out.

---

### Post by ls8 on 2010-11-15
Can you post a link to the bugreport, please?

---

