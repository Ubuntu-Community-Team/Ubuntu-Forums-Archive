---
title: "Netgear WG311T modules load, no interface"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by daigidan on 2006-06-18
Greetings,

I am a longtime Debian fan who decided recently to build a MythTV box and found Ubuntu to be a great fit. I'm using a Netgear WG311T and the modules for it appear to load...

lsmod | grep ath
ath_pci                89760  0
ath_rate_sample        19984  1 ath_pci
wlan                  154228  2 ath_pci,ath_rate_sample
ath_hal               173680  2 ath_pci,ath_rate_sample

...but ifconfig and iwconfig don't show the ath0 interface. dmesg gives me:

ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
wlan: 0.8.6.0 (EXPERIMENTAL)
ath_rate_sample: 1.2
ath_pci: 0.9.6.0 (EXPERIMENTAL)

I'm at a loss here and am starting to question whether I bought the wrong card. Any suggestions are greatly appreciated.

Cheers,
Sean

---

### Post by daigidan on 2006-07-06
Ended up fixing this by using a different atheros-based NIC and madwifi picked it up like a charm, even worked with WEP with no issues. :]

~Sean

---

