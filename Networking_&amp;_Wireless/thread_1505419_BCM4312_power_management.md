---
title: "BCM4312 power management"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by mikewhatever on 2010-06-09
When I run **sudo iwlist eth1 txpower**, the output is as follows:
```
eth1      2 available transmit-powers :
	  0 dBm  	(1 mW)
	  25 dBm  	(255 mW)
          Current Tx-Power:32 dBm  	(1496 mW)

```

Now, 1496mW is rather high and I'd like to switch to 255mW, at least when on battery. 
However, **sudo iwconfig eth1 txpower 255mW** produces the error:
```
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Operation not supported.

```
Anyone knows how to do it?

---

### Post by mikewhatever on 2010-06-10
bump):P

---

### Post by mikewhatever on 2010-06-11
bump:|

---

### Post by mikewhatever on 2010-06-12
bump

---

### Post by mikewhatever on 2010-06-13
bump

---

### Post by mikewhatever on 2010-06-14
bump

---

### Post by mikewhatever on 2010-06-15
bump

---

### Post by mikewhatever on 2010-06-17
:popcorn:

---

### Post by mikewhatever on 2010-06-18
It's been a week and 153 views. This is the last bump.

---

### Post by mikewhatever on 2010-07-20
The workaround - use b43 instead of sta in Karmic. You'll also need 'linux-backports-modules-wireless-karmic-generic' installed, otherwise the b43 driver doesn't work.
Here is the txpower level with b43 in Karmic:
```
sudo iwlist wlan0 txpower
wlan0     unknown transmit-power information.

          Current Tx-Power=20 dBm  	(100 mW)


```

Lucid doesn't have that problem with the sta driver.

---

