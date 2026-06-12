---
title: "Slow Wifi on Toshiba Satellite L30-109"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by jiti2 on 2013-08-29
Hi all !
I've just made a fresh install on my Toshiba Satellite L30-109, everything works but the wireless.
It's very slow...
Any idea ?
Thanks ! :D

---

### Post by jiti2 on 2013-09-01
This works :

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
sudo gedit /etc/modules

---

