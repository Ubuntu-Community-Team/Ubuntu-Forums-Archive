---
title: "Broadcom 4312 Wireless"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by Leprkan on 2011-01-15
Well, this is evidently a widespread problem since there's a sticky for it.  Anyway, I tried the melange of solutions on that thread with no results.  I think I need a more guided hand so if there are any willing here's what I'm working with:

The facts:
-Ubuntu 10.10
-lsmod shows wl running
-lshw and lspci -C network confirms the chipset
-iwconfig shows lo, eth0, and eth1 (which is apparently the wireless port)
-Running the Broadcom STA drivers
-firmware-b43-lpphy-installer installed
-b43-fwcutter installed
-iwlist scan works 

The symptoms:
-The network-manager shows that wireless is disabled
-When left-clicked the option to enable wireless is grayed out

Hence, I am unable to get wireless.

Any help appreciated. Further information available on request.

Thanks
Leprkan

---

### Post by kn0w-b1nary on 2011-01-15
I ran into a similar problem once, the fix?
Fn+F2 (equivalent to sliding the Wi-Fi switch)

You might want to check that. :P

---

### Post by nm_geo on 2011-01-15
Try this in terminal 

```
rfkill list
```Then show the results.

---

