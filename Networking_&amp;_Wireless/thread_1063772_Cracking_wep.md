---
title: "Cracking wep?"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by sinogap on 2009-02-08
is it possib le to crack wep with this?
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315]
is yes? what tool? how? is it possible?
if no? when will it be possible?

---

### Post by dburnett77 on 2009-02-08
> **sinogap said:**
> is it possib le to crack wep with this?
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315]
is yes? what tool? how? is it possible?
if no? when will it be possible?

How these posts proliferate is beyond me, but air-crack is in the repositories.

Tell them via email to buy a RadioShack Wifi Locator for about $5.95US so they can stomp your ***.

---

### Post by sinogap on 2009-02-08
> **dburnett77 said:**
> How these posts proliferate is beyond me, but air-crack is in the repositories.

Tell them via email to buy a RadioShack Wifi Locator for about $5.95US so they can stomp your ***.

can anyone actually offer advise

---

### Post by sinogap on 2009-02-09
bump

---

### Post by cybergurra on 2009-02-09
should be possible if the network interface allows you to put it in promiscuous mode, try the backtrack linux suite, works just fine.
regarding your question on how to do it, just google "linux wep crack" or something similar..

---

### Post by Ayuthia on 2009-02-09
At this point the only modules you are able to use is the wl and ndiswrapper modules.  Neither one of these modules can switch to monitor mode and as far as I know none of the cracking tools provide support to those modules.

---

### Post by HavocXphere on 2009-02-09
> **sinogap said:**
> can anyone actually offer advise
Nope, but if you know anyone who is handing out bank-robbery instruction kits then let me know.:rolleyes:

---

### Post by kevdog on 2009-02-09
Just want to clear up some questions

wl - can not run Monitor Mode
ndiswrapper - can definitely not run Monitor Mode
b43 - Can run Monitor Mode
openwwl- ???

Ayuthia or anyone else, can you verify this list?

---

### Post by bapoumba on 2009-02-09
Is this your own network you want to crack for educational purposes ? You can PM me with the answer.
Closing for now, sorry.

---

