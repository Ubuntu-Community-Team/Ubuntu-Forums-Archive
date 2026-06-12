---
title: "Network Manager Not Recognizing Wireless"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by mastermindg on 2010-01-27
I've using the RT2870 module to run my WUSB600N adapter. The adapter is working as expected, the essid is grabbed by the RT2870 driver and DHCP is relayed thru the networking script. RT2870 was built for network manager with the following settings:

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

My network is up and working fine; however, the Network Manager Applet is not recognizing this. I created a Wireless Connection under Network Manager and it was able to scan for networks and I set it. However it's showing as Never being used.

Any ideas?

---

### Post by mastermindg on 2010-01-27
I ended up replacing it with wicd. This is more for aesthetics as my connection is stable and doesn't require administering.

---

