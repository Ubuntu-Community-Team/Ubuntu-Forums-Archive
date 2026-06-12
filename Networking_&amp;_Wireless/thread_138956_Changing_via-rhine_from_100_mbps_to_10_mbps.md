---
title: "Changing via-rhine from 100 mbps to 10 mbps"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by manish_m on 2006-03-02
hi
I have via-rhine ethernet controller, it working under breezy. I share internet connection with my friend. The broadband comes at 10 Mbps but the ethernet card is working at 100 Mbps & hence internet is very slow. I acutally verified by changing the flow control settings in winxp. So, has anybody got any idea how can i fix this?

---

### Post by claes on 2006-03-03
Try the mii-diag tool.

sudo mii-diag ethX -F 10baseT-HD

The tool comes from mii-diag package not sure if it's installed by default.

Claes

---

