---
title: "wireless STILL slow. any ideas?"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by michiganitis on 2011-05-07
Installed 11.04 on my Acer Aspire 5742-6674. It has a Atheros adapter. In my Windows 7 partition, its a AR5B95. But Ubuntu is says its a AR9287.

I'm using the ath9k driver, version 2.6.38-8-generic-pae.

I tried the following:

```

sudo -s

echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf

reboot

```

Still not working right. My wifi works ok at first...gets slower and slower...and eventually times out on everything. At that point, I have to restart the computer so it can work normally for a short time.

Works totally fine when wired. Works totally fine wired or wireless on my Windows 7 partition. Both wired and wireless worked fine when I was using 10.10.

Any ideas? Thanks!

---

### Post by uncaspi on 2011-05-07
Try to turn off power save mode.
sudo iwconfig wlan0 power off txpower 20
assuming your card is wlan0

---

