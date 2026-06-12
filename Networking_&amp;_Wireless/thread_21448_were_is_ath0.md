---
title: "were is ath0"
date: 2005-03-22
forum: Networking &amp; Wireless
---

### Post by AP81 on 2005-03-22
My wifi card (DLINK DWL-G520 atheros chipset) was detected on wlan0 (not ath0) during install and still doesn't work.  Using iwconfig on wlan0 doesn't seem to detect the correct speed and fails if I run 'sudo dhclient wlan0'.    I tried my other card (Netgear- also atheros), and it also detects on wlan0 with the same problems.

I have got both cards running perfectly on Slackware using Madwifi.  What have I done wrong?  I thought a simple:

'sudo modprobe wlan'
'sudo modprobe ath_hal'
'sudo modprobe ath_pci'

would do the trick, but iwconfig doesn't show any ath0 there.  Any ideas?

Thanks in advance.

---

### Post by mkeuter on 2005-03-29
you need the linux-restricted-modules for your kernel, this will install the madwifi halwrapper.. this worked for me under warty 
Update
this package does also exist in hoary...

---

