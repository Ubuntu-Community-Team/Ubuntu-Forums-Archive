---
title: "shut wireless off"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2009-09-07
i have tried unchecking Enable _W_ireless but it still uses power
i would like to shut it off when im not using it especially if im using battery power

---

### Post by jward3010 on 2009-09-07
This should help as well (whether it'll kill the power or not I don't know):
Open a terminal and type```
sudo ifconfig "device-name" down
```
where "device-name" is the name of your wireless device (could be wlan0, ath0, ath1, eth0, eth1)

If you don't know you wireless devices internal name, paste the output of iwconfig here (preferably in [CODE] tags).

---

### Post by pqwoerituytrueiwoq on 2009-09-08
```
sudo ifconfig "device-name" up
```  that will turn it back on right?

---

### Post by jward3010 on 2009-09-09
> **pqwoerituytrueiwoq said:**
> ```
sudo ifconfig "device-name" up
```  that will turn it back on right?

YEP, you may need to wait a few seconds for the device to come up again and start scanning for networks though.

---

