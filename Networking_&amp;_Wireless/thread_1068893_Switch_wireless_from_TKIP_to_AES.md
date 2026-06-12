---
title: "Switch wireless from TKIP to AES?"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by tonystark on 2009-02-13
I have a dual-boot system with a DWL-G650 card.

My router has two WPA Personal security modes: AES and TKIP

When I boot my laptop to WinXP, the laptop and DWL-G650 card will work in either AES or TKIP mode (as long as both the router and card are set to the same mode).

When I boot to Ubuntu 8.04, it works fine in TKIP mode.

Unfortunately, my wife's MacBook only works in AES mode.  So I'd like to use the AES mode on the router.

However, I don't know how to turn on the AES mode under Ubuntu, and I don't see any way to change using the "Network Settings" window.

---

### Post by tonystark on 2009-02-13
By upgrading all of the firmware in all of the hardware, I was able to get WPA2 working on all of the machines concerned, so that has solved my problem.:KS

---

### Post by awellstead on 2009-05-12
Bump on this. I'm glad tonystark was able to deal with his issue, though I'm in the same boat. I've got everything else humming with AES, but my iwlist scan is coming back to me with my solo-boot 8.10 ciphers at TKIP.

Any idea how to get that to AES?

---

### Post by mattshow on 2009-07-09
I have the same question, but for different reasons.

My router has a "TKIP and AES" mode, which is supposed to negotiate which protocol to use and use AES when available. However, when I do this, my laptop always uses TKIP and it seems like the proprietary Broadcom drivers don't place nice with TKIP. My connection to my wireless router is intermittent, and during the outages, I get lots of 

TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4218600

messages in my dmesg output. 

If I set the router to only support AES, it works fine, but I'd rather set the router to support both TKIP and AES, to support more devices connecting to the network. Is there a way to tell Ubuntu to use AES and not TKIP?

---

