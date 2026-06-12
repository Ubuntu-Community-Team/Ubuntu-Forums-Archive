---
title: "Trouble with Hidden network"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by Synoc on 2012-06-14
I turned off the SSID beacon on my wireless router. Before hand, my box would connect straight away. after I turned off the beacon it sometimes takes up to a full 2 minutes or more to find it and connect. I can speed up the process by disabling the wireless adapter and reenabling through the NetworkManager icon. 

output of "lspci | grep Wireless"

```
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01) 
```

the only hint at anything I find in dmesg is ```
[   15.409466] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
```

---

