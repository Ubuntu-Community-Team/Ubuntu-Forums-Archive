---
title: "Multiple USB 3G Dongles with bandwidth management"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by RaisinBoy on 2011-11-28
Hi there,
 
Hope that somebody out there is also giving this a go, or has some advice to share...
 
There is a special going, which gives me 10GB of 3G data for a steal of a price... I need about 30GB a month, so what I would like to do, is build a box that would allow me to connect 3 USB 3G dongles, and then set the box to use 10GB from USB dongle 1, when depleted move onto dongle 2, then 3 automatically (4,5,6,7). But NOT to go over the 10GB limit so as to avoid paying the exorbitant out of bundle rates.
 
Is there a way to do this?
 
:)

---

### Post by Drenriza on 2011-11-28
If you set this up with a Ubuntu box. Isin't it then a question of connecting all 3 devices and shutdown all ports in ifconfig. Then open the first port and monitor packages received. When packages received is == 10GB shutdown the port and move to the next one, and do the process again.

---

### Post by RaisinBoy on 2011-11-28
Hi Drenriza,
 
Thanks for the quick reply... Ok, what you propose sounds logical, but how do I automate this? The monitoring part that is, so that I don't need to keep checking the logs to see if I need to shutdown one port and enable the next. Sorry if I am just ignorant and this can all be done in ifconfig...

---

