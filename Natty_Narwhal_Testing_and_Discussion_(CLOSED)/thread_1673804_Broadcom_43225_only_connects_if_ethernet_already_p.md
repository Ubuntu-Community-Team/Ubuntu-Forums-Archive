---
title: "Broadcom 43225 only connects if ethernet already plugged in"
date: 2011-01-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by razmakati on 2011-01-23
Hello all,

Natty updated as of 22 Jan 2011. Using an Hp Mini 210 with a BCM43225 card and the Broadcom STA restricted driver. Wireless will only connect to an unsecured or secured essid if the ethernet cable is plugged in. The new FOSS brcm80211 driver is the same. 

Nm-Applet can see access points from cold boot as well as when ethernet is plugged in. If wireless is connected it will reconnect from suspend as well as toggling the wireless switch.

Anyone else seeing this with Broadcom cards or know if there is a bug report

Anymore info needed?

Thanks

---

### Post by ronacc on 2011-01-31
I've also been seeing this lately with my rtl-8180 so its not just broadcom . Also I don't think that wireless is really connected it just shows that way , if you use indicator-applet to disconnect ath0 wireless dissapears too but it doesn't say its doing it .

---

