---
title: "wl load problem ( broadcom-sta for BCM4313)"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by hamidk on 2010-10-31
Now  I`m feeling completely lost!
In brief I've messed it:

while trying to find a way to enable packet-injection and RFMON on my card, I seems to have destroyed even basic functionality.

Before this, wifi was wirking prefectly through Broadcom-STA driver (Ubuntu 10.10 x64).
while trying to re-build the b43 and wl driver, seems something went wront that even normal kernel module fails to load : 

---
**# modprobe wl**
FATAL: Error inserting wl (/lib/modules/2.6.35-22-generic/updates/dkms/wl.ko): Invalid argument
FATAL: Error running install command for wl

---

**Tail of /var/log/messages :**
---
Oct 31 21:13:46 unknown kernel: [ 3683.845151] wl: disagrees about version of symbol lib80211_get_crypto_ops
Oct 31 21:13:46 unknown kernel: [ 3683.845160] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
Oct 31 21:14:16 unknown kernel: [ 3713.465780] wl: disagrees about version of symbol lib80211_get_crypto_ops
Oct 31 21:14:16 unknown kernel: [ 3713.465789] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
---



This seems happened after I tried to use "module-assistant" utility, to manage the broadcom-sta , and it messed things. 

Before using module-assistant , I was playing with latest wireless-compat drivers package, trying various configs, but everything was fine and "wl" were loadable any time BEFORE I try module-assistant utility. 

I've tried to completely removing broadcom drivers & building everything from scratch, and also trying same process through ubuntu software manager. GUI "Aditational Drivers" utility shows the broadcom-sta available but mention it '*activated but currently not in use*' . 

I've also tried to rmmod b43 and other related modules & reloading wl, and also trying to blacklist b43 etc... no success. 


Can anybody comment where should I back-trace and solve this problem?


//
# lspci -nn |grep Bro
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
# uname -a
Linux unknown 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
//

---

### Post by hamidk on 2010-10-31
Ok ,the problem seems to be solved .

I followed hints from this thread : 
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630)

BUT simply removing backport packages did NOT helped me.
one of backport packages was not uninstalling, so I had to use 'dpkg --force-all -P'
and after that , I got warning about some directories not deleted due to being not empty.
manually removing them (containing modules causing trouble reported by dmsg) and re-installing broadcom-sta drivers 
by **'apt-get install --reinstall bcmwl-kernel-source'**  and 'modprob wl' solved the case .

---

### Post by p0ntiac on 2013-01-26
Hamidk, your infos helped me to solve my wifi problem, thanks =D>

---

### Post by wildmanne39 on 2013-01-26
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old.

---

