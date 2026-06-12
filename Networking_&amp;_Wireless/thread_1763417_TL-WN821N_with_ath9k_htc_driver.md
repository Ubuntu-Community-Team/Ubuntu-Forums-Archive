---
title: "TL-WN821N with ath9k_htc driver"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by 1986shemesh on 2011-05-20
Hello,

I have a new TL-WN821N wireless (usb), it has a Atheros AR7010+AR9287 chipsets, I install compat-wireless driver (with the "driver-select" script, I only installed ath9k_htc modules), I did everything this guide says:

[http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc)

- Added htc_7010.fw file to /lib/firmware.
- Did the modswitching tweak for htc_7010.

I only have problem with "Configuring your kernel" part, can someone please help me this part, I don't know how to config my kernel, and can't find good(!) guide on how to do it.

I have ubuntu 11.04.

thank you,
Assaf.

---

### Post by 1986shemesh on 2011-05-21
someone?

How do I enable these options in your kernel config:

CONFIG_ATH_COMMON=m
CONFIG_ATH9K_HW=m
CONFIG_ATH9K_COMMON=m
CONFIG_ATH9K_HTC=m

thank you,
Assaf.

---

