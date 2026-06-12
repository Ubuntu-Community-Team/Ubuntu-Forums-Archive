---
title: "Network Manager munging WPA password?"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by sehrgut on 2009-03-06
I seem to be having a problem with Network Manager's use of WPA key. I'm using a Dell Latitude C400 with Broadcom wifi, and the driver (b43) works just fine. (I'm posting from it, actually.)

The problem appears to be with Network Manager. When NM prompts me for the WPA key, I type in, (for example) **0123!abcd**. It then attempts to connect to the network, fails, and prompts again for the password. In the meantime, it's converted the password to a hexadecimal string of some derivation. No matter how many times I attempt this, either allowing it to use its hexification of the password or retyping the password, it can't connect.

If, however, I first issue:

```

$> sudo iwconfig wlan0 essid campus key s:'0123!abcd'
$> sudo ifconfig wlan0 down && sudo ifconfig wlan0 up

```

The next time I attempt to connect to the network via Network Manager, it connects just fine. Any ideas on how to do the equivalent of the above actions from within Network Manager so that it'll "just work"?

---

