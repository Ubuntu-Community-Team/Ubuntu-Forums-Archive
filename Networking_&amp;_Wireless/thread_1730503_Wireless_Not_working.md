---
title: "Wireless Not working"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by sidjajodia on 2011-04-16
I am using HP pavilion DV 2002tu model laptop. I am not able to use wireless device on ubuntu for wi fy internet surfing. My driver is not getting detected. How shall I go about resolving this problem?

---

### Post by KegHead on 2011-04-16
Hi!

Try:

system..admin..additional drivers.

KegHead

---

### Post by pawan98 on 2011-04-16
jj

---

### Post by varunendra on 2011-04-18
> **sidjajodia said:**
> I am using HP pavilion DV 2002tu model laptop. I am not able to use wireless device on ubuntu for wi fy internet surfing. My driver is not getting detected. How shall I go about resolving this problem?

Try first what KegHead suggested. If that doesn't help, please post back the results of following commands:
```
sudo lshw -C network
```
```
iwconfig
```

---

### Post by Gotlieb on 2011-04-18
Hi,

Do you have the latest updates? What distribution are you using? I had the same the problem using Karmic 9 but a fresh upgrade worked.

Hoping the terminal cmd you just got helps.

---

