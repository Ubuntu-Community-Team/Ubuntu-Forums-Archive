---
title: "can i improve my wireless driver?"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by yumgnomeandthensome on 2009-12-31
I am running ubuntu 9.10 using an hp laptop with driver details as follows:
cmd - lspci | grep Network
Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

cmd - wpa_supplicant -helpTo
drivers:
  wext = Linux wireless extensions (generic)
  nl80211 = Linux nl80211/cfg80211
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wired = wpa_supplicant wired Ethernet driver

I would just like to know if I can improve on the driver or if I can rest assured that the native install is all i need?
Regards, Evan

---

### Post by yumgnomeandthensome on 2010-01-02
i've since installed 'wcid' for managing my wireless connection. 
so far after 5 reboots it has connected as my pc boots up without fault.

---

### Post by teward on 2010-01-02
you can't improve the wireless driver for Intel wifi cards.  you're stuck with the generic drivers.  they work, I've got the generic Linux drivers for my Intel A/G/N card in my Dell, and they work perfectly.

---

