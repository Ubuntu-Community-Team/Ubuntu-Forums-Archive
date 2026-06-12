---
title: "need help with atmel-chipset seriously!!!"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by soc on 2006-06-29
hi, i help a friend of mine to convert to linux.
is asked him before if he had any problematic devices like brand-new graphic card, wireless - he denied ... but no, after he installed dapper he told me that his cameo wlg-1500 usb wireless adapter wasn't working. *grrrr*
so i'm just trying to get it working ... but i haven't even found any information which chipset is in this weird cameo-crap.

later i let him install "atmel-firmware" because some older usb adapters of cameo used some atmel chipset... but when he rebooted it wouldn't even boot anymore!!!!
it just stayed 10 minutes saying "loading hardware drivers", after that he rebooted and took his 386 kernel.

how do i fix this?
please i need help!!!

---

### Post by Eversmann on 2006-06-29
It doesn't work with ndiswrapper?

---

### Post by tturrisi on 2006-06-29
[http://linux-wless.passys.nl/query_part.php?brandname=Cameo](http://linux-wless.passys.nl/query_part.php?brandname=Cameo)

---

### Post by soc on 2006-06-29
i had this website, too. "unknown" ... great ... *sigh*

---

### Post by soc on 2006-06-30
my friends adapter (wlg-1500) isn't even mentioned. :-(

---

### Post by tturrisi on 2006-06-30
The older devices use the ACX chipset & it may very well be used in your friend's device.  See:
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

---

### Post by soc on 2006-07-02
thanks!!! i will look into it.
is there a chance to find out which chipset is used in this card??? maybe in some logfiles?

---

### Post by Twinxor on 2006-07-12
> **soc said:**
> thanks!!! i will look into it.
is there a chance to find out which chipset is used in this card??? maybe in some logfiles?

It will be listed in the system log. Unplug and replug the wireless device, and then type 'dmesg' in the console.

---

### Post by seek3r on 2007-06-28
Some of the old cameo cards used the Marvell Chipset, maybe that helps 

(wlg 1101 specifically, dont know about the newer ones)

---

