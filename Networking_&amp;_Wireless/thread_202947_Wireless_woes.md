---
title: "Wireless woes"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by MrGreen on 2006-06-24
Hi,

Have got wireless network up & running on my laptop but connection seems very slow ... pages take up to a minute to load

lspci shows

```
0000:06:05.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
```

lsmod

```
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  3 ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
```

Under Xp pages load quickly ... wondered if its a linux driver problem?

Is there anything I can do to make sufing quicker ?

TIA

---

### Post by mvaranda on 2006-06-25
Yup.  I have same problem only in my laptop with Atheros (MADwifi driver) other laptops with Intel ipw2200 and Broadcom work fine.
There are a couple posts about it as well as a bug report being already filed.

---

### Post by MrGreen on 2006-06-25
thanks for that, I will keep looking ......

---

