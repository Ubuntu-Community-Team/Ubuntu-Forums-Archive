---
title: "Wireless Broadcom Problem ):"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by ZaNiuM on 2010-06-06
I try to setup my wireless card, by using "broadcom sta" in the program hardware drivers, but it always fails when installing and tells me to "Please have a look at the log file for details: /var/log/jockey.log"


Help please.

---

### Post by purelinuxuser on 2010-06-06
Post the contents of the file /var/log/jockey.log.  Either copy and paste to your reply via Ethernet, or save it on a flash drive.  Don't forget to use the [CODE] tags ;)

---

### Post by ZaNiuM on 2010-06-06
```
2010-06-06 19:53:30,651 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-06 19:53:30,750 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

---

### Post by YBratlien on 2010-06-06
I think I had a similar problem, though I can't recall what the log said.

The issue was that you first have to connect to the internet using a wired connection before you can download the drivers.

---

### Post by ZaNiuM on 2010-06-06
> **YBratlien said:**
> I think I had a similar problem, though I can't recall what the log said.

The issue was that you first have to connect to the internet using a wired connection before you can download the drivers.

Already tried that multiple times :/

---

### Post by purelinuxuser on 2010-06-06
Plug into Ethernet and update your system (System > Administration > Update Manager).  Then try to redownload the driver.

---

### Post by ZaNiuM on 2010-06-06
> **purelinuxuser said:**
> Plug into Ethernet and update your system (System > Administration > Update Manager).  Then try to redownload the driver.
Did that and still says the same thing.

---

### Post by purelinuxuser on 2010-06-06
Okay, guess we'll have to go with a different driver!  Plug into Ethernet, and open Synaptic (System > Administration > Synaptic Package Manager).  Install the package "b43-fwcutter."  You will get a prompt with a checkbox that says "Automatically download and install firmware?"  Make sure it is **checked**.  Then reboot.

Wireless *may or may not* work.  If it doesn't, post the output of
```
ls /etc/modprobe.d/blacklist*
```

---

### Post by sille777 on 2010-06-06
Dont know if you tried this yet, but it might help you verify what driver you need and get it properly installed.  this site is what got my wireless working (broadcom chipset.): 

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by ZaNiuM on 2010-06-06
> **purelinuxuser said:**
> Okay, guess we'll have to go with a different driver!  Plug into Ethernet, and open Synaptic (System > Administration > Synaptic Package Manager).  Install the package "b43-fwcutter."  You will get a prompt with a checkbox that says "Automatically download and install firmware?"  Make sure it is **checked**.  Then reboot.

Wireless *may or may not* work.  If it doesn't, post the output of
```
ls /etc/modprobe.d/blacklist*
```
I love you, thanks very much (:

---

### Post by purelinuxuser on 2010-06-06
:lolflag: That's one of the very few times when that procedure has actually worked for me :D

Don't forget to slap a [SOLVED] tag on this thread ;)

EDIT: 100th post w00t!!!

---

