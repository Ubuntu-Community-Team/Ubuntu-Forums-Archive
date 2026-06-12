---
title: "HP Mini 1001tu wireless connection problem using Ubuntu 9.10"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by badaveil on 2010-01-31
I successfully did a dual boot on a HP Mini 1001TU netbook. However, the wireless doesn't connect. Over the internet, someone had a similar problem with his Dell notebook using a Karmic and said that Karmic has a bug that doesn't install the "Broadcom STA wireless Driver" and recommended a prerequisite wired internet connection then the following command line:

sudo apt-get update
sudo-get -reinstall install bcmwl-kernel-source

followed by a reboot which solves the problem.

I would like to try this out but the netbook only accepts a USB -router connection but my router doesn't have a USB port.

Does anyone know I can solve this problem? Thanking you in anticipation of.

---

### Post by gregp123 on 2010-07-07
I have spent the whole night trying to fix the same problem , only possible fixes (iv'e tried the above, and variations from forums that don't work, get error messages) look like these, which i haven't tried yet.
[http://www.tomshardware.com/forum/237028-50-ubuntu-mini-1000-wireless](http://www.tomshardware.com/forum/237028-50-ubuntu-mini-1000-wireless)
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
these look pretty tedious and involved however.
please let me know if you get anywhere, it is really dissappointing to not have wireless on the hp mini 1001 tu, i don't reaaly want to put xp back on it, that is just tedious with defrag +antivirus.

---

### Post by gregp123 on 2010-07-07
I forgot to mention , i do have usb modem intrernet connection, also tried with bootable usb as a software source, rediculous.

---

### Post by bkratz on 2010-07-07
> **badaveil said:**
> I successfully did a dual boot on a HP Mini 1001TU netbook. However, the wireless doesn't connect. Over the internet, someone had a similar problem with his Dell notebook using a Karmic and said that Karmic has a bug that doesn't install the "Broadcom STA wireless Driver" and recommended a prerequisite wired internet connection then the following command line:

sudo apt-get update
sudo-get -reinstall install bcmwl-kernel-source

followed by a reboot which solves the problem.

I would like to try this out but the netbook only accepts a USB -router connection but my router doesn't have a USB port.

Does anyone know I can solve this problem? Thanking you in anticipation of.

If you have a "live" cd ( installation?) you should be able to get the file you want in a similar manner to this posting--although it was referencing 9.10

[http://ubuntuforums.org/showthread.php?p=8123042#post8123042](http://ubuntuforums.org/showthread.php?p=8123042#post8123042)

---

