---
title: "Lenovo B570e drops connection  after 2-5 min,"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by a.sopco on 2012-08-29
Hello guys!

I can't solve this problem by my own.  My wireless connection drops after 2-5 min.
I try turn off "power management", switch to Wicd,  disable encryption, but nothing works

Lenovo B570e
ubuntu 12.04 LTS
Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

What else  can  I do?

---

### Post by praseodym on 2012-08-29
Disable the hardware encryption of the "ath9k" driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Change the encryption to WPA2 only.

---

