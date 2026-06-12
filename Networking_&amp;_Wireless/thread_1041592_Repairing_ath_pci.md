---
title: "Repairing ath_pci"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by davidwashere2003 on 2009-01-16
Hello, I was trying things to get my wireless going and picked up the following commands off one post:

sudo modprobe -r ath_pci
sudo modprobe ath_pci led=1

Now when I run dmesg and sudo modprobe ath_pci I get...

```
[  598.953351] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  598.988641] wlan: 0.9.4
[  599.005067] ath_pci: Unknown parameter `led'
[  622.053058] wlan: driver unloaded
[  622.073064] ath_hal: driver unloaded
[  635.255968] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  635.290956] wlan: 0.9.4
[  635.307354] ath_pci: Unknown parameter `led'
[  648.451524] ath_pci: Unknown parameter `led'
[  661.994402] ath_pci: Unknown parameter `led'
[ 1179.897479] ath_pci: Unknown parameter `led'
[ 1628.656394] ath_pci: Unknown parameter `led'
a@a-laptop:~$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.27-7-generic/volatile/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
a@a-laptop:~$
```

How can I repair ath_pci so the errors are gone?

---

