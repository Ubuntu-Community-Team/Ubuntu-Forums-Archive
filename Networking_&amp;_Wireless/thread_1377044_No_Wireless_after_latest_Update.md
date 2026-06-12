---
title: "No Wireless after latest Update"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Statik on 2010-01-09
Hi,

Creating a new thread for the specific chipset.

Laptop is an Acer 5534 with the Atheros chipset. Normally uses the Ath9k driver. To get it to work originally I had to download, compile and install the latest compat_wireless drivers. See post here:
[http://ubuntuforums.org/showthread.php?t=1311832](http://ubuntuforums.org/showthread.php?t=1311832)

I did the update that came through today and after the reboot there was no wireless internet. It alternates between reboots between having no wireless networks at all detected to never connection to the [AUTO] network previously defined.

To fix the problem, I downloaded the latest compat_wireless, compat-wireless-2009-12-11.tar.bz2, and followed the same procedure. I did not do a make clean.

To solve the problem temporarily, I edited the grub config and set default to 2 instead of 0 (1 would be 0 in recovery mode).

Any help would be appreciated.

Statik


= = = = =
Mörgæs 2013-12-05:
Using Lubuntu 13.10 everything works in first attempt.

---

### Post by chili555 on 2010-01-09
Would you please do:```
cd compat-wireless-2009-12-11/
make clean
./scripts/driver-select ath9k
make
sudo make install
sudo reboot 
```Do you get any errors? Warnings are OK. If the behavior continues, please do:```
dmesg > gmesg.txt
zip -r dmesg.zip dmesg.txt
```Attach dmesg.zip to your reply.

---

