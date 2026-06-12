---
title: "Wireless access points"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by Reddoug on 2010-03-21
Hi 

Is there away to view wireless access points without being connected. I am having trouble getting connected to my wireless DSL modem. I have no problems connecting with Windows Vista. Just can not get Ubuntu 9.10 to connect. iwconfig says no associated with access point. I can connect with ethernet cable.

Thanks, Doug

---

### Post by iponeverything on 2010-03-21
run:
```

sudo iwlist scan
```

---

### Post by Reddoug on 2010-03-22
Hi

Output from sudo iwlist scan command.

Cell 01 - Address (mac address)
          Channel:9
          Frequency:2.54
          Quality=65/70 Signal level=-45 dBm
          Encryption key:on
          ESSID;""
          Bit Rates  (a list of them)
          Mode:Master
          Extra:tsf=0000002b171c122
          Extra: Last beacon: 3488ms ago
          IE: unknown:  (6 rows of these)

Looks to me like it is seeing my wireless router. Just can not associate with it. 

Thanks, Doug

---

### Post by Reddoug on 2010-03-26
Hi

Finally figured out my problem. I use WEP and had a 64 bit key. I did not realize in Unbuntu when I set it for 40-128 bit keys it meant it had to be 40 OR 128 bit key. Changed my modem to 128 bit and everything works. 

Thanks, Doug

---

