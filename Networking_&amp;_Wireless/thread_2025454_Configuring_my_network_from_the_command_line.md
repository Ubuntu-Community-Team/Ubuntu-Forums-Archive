---
title: "Configuring my network from the command line"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by ox10 on 2012-07-14
](*,) [FONT=Georgia][COLOR=darkred]Hello,[/COLOR][/FONT]
[FONT=Georgia][COLOR=darkred]How do I configure my network (ethernet and wifi) from the command line outside of the network manager? Can you point me to any resources where this is explained?[/COLOR][/FONT]

---

### Post by Cheesehead on 2012-07-14
Assuming your interfaces are wlan0 (wifi) and eth0 (ethernet). Your interface names may differ. Use  [FONT="Courier New"]ifconfig -a[/FONT]  to find them.

To bring interfaces up manually
```
iwconfig wlan0 essid <network-name>
ifup wlan0

ifup eth0
```

To bring interfaces down manually
```
ifdown wlan0
ifdown eth0
```

---

### Post by chili555 on 2012-07-14
If Network Manager is installed, it is very unlikely that you can control your networking interfaces with the command line. Even if you kill the process, it re-spawns.

---

### Post by Kirk Schnable on 2012-07-15
> **chili555 said:**
> If Network Manager is installed, it is very unlikely that you can control your networking interfaces with the command line. Even if you kill the process, it re-spawns.

True, and I wouldn't recommend uninstalling network manager without a good reason. 

I should also note, Cheesehead's instructions are a great starting point, but his wireless instructions will only work for open/insecure wireless networks. The commands are different for WEP or WPA encrypted networks, but we can help with those too if necessary. 

Kirk

---

