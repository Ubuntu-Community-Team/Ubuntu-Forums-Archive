---
title: "Set modulation 11g on iwl3945"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by dryphi on 2011-08-27
Is there a way to force the Intel 3945ABG card w/ driver iwl3945 into a specific modulation mode? 802.11G for instance? Instead of the auto a/b/g
I tried
```
sudo iwconfig wlan0 modu 11g
```
And got an error like the following:
SET failed on device wlan0 ; Operation not supported.

---

### Post by praseodym on 2011-08-28
You should easily be able to change the router setting to "g"-mode alone.

Or have a look at

```
man wireless
```
and the links therein

---

