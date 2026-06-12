---
title: "wireless issues - ath5k"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by jaminotte on 2010-08-08
after upgrade to 10.04 my wireless card was unusable.  

following the advice here--> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090)
i ran:

```
sudo modprobe ath5k nohwcrypt
```Perfect, everything works great!  I was thinking i got out of the whole deal way too easy.  To make it stick each time i boot, i ran this:

```
sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf"

```Honestly, i don't remember the outcome immediately after i did it, but everything was still working.  After a reboot the wireless was again not working.  


now, if i run 
```
sudo modprobe ath5k nohwcrypt
```i get:
```
FATAL: Error inserting ath5k (/lib/modules/2.6.32-24-generic/updates/cw/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```if i run:
```
sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe. d/custom-wireless.conf"
 
```i get nothing

maybe i made a typo in the second thing i ran??  what the heck did it do? any help is appreciated, i really have no idea what i'm doing.  

thanks, 
Jamin

---

