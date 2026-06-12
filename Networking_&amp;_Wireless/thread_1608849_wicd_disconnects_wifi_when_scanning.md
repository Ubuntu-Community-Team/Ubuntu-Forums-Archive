---
title: "wicd disconnects wifi when scanning"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by claracc on 2010-10-29
Hallo,

I have an hp compaq 6720s laptop dualboot vista/ubuntu lucyd.

My wireless card is Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02), controlled by wicd 1.7.0 (gnome network manager connects/disconects the net continuously).

The problem is, any time I do a scanning with wicd or from command line to see the wifi nets around, my wireless is disconnected, then it connects again because is set to automatic reconnection.

Could I fix this behaviour?

Thanks in advance

---

### Post by DirtyPC on 2010-10-29
> **claracc said:**
> Hallo,

I have an hp compaq 6720s laptop dualboot vista/ubuntu lucyd.

My wireless card is Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02), controlled by wicd 1.7.0 (gnome network manager connects/disconects the net continuously).

The problem is, any time I do a scanning with wicd or from command line to see the wifi nets around, my wireless is disconnected, then it connects again because is set to automatic reconnection.

Could I fix this behaviour?

Thanks in advance
Generally yes, mine does this also, I dont think you can connect to a network and scan at the same time with Wicd, the stock network manager just had a refresh button I think. You could just unclick auto connect if you don't want it to connect back again

---

### Post by claracc on 2010-10-30
So, the conclusion is wicd cannot mantain wifi connection when scanning?. I don't think this is the desirable behaviour. Perhaps I'll report it as a bug in wicd.

Wicd also has a refresh button, anytime I click on refresh, wicd disconnects wifi.

Regards

---

