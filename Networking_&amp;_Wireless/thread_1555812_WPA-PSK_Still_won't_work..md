---
title: "WPA-PSK: Still won't work."
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Nanix on 2010-08-18
My wireless card is fully supported in Ubuntu (RT2800 802.11n PCI) and functions perfectly under a WEP open network. However, my home network is WPA-PSK+WPA2-PSK (ultimate compatability) and it refuses to connect. It keeps asking for the key and then never successfully connects. 

I have the latest 64bit Ubuntu from the front page. I have all of the wireless utilities: wpasupplicant, network manager
I have tried editting the strings under Configuration Editor. No success.

Any assistance? I really want to get this up and running.

---

### Post by Nanix on 2010-08-19
I read that the combing WPA+WPA2 might cause some problems, so I switched to WPA2 only, with no success.

---

### Post by bkratz on 2010-08-19
> **Nanix said:**
> I read that the combing WPA+WPA2 might cause some problems, so I switched to WPA2 only, with no success.



I had that problem too and that worked for me but I also had to chose AES only, not TKIP and AES.

---

### Post by Nanix on 2010-08-19
> **bkratz said:**
> I had that problem too and that worked for me but I also had to chose AES only, not TKIP and AES.

Tested this, still no luck. I appreciate the input though!

---

