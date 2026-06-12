---
title: "Acer Aspire One / Lucid 10.04 - wireless greyed out"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by qprfact on 2010-08-03
My son's Acer Aspire has recently decided to no longer allow him to enable wireless. It has worked in the past (and that includes on this version of Ubuntu), but it steadfastly refuses now.

This guide [http://swiss.ubuntuforums.org/showthread.php?t=1316126&page=4](http://swiss.ubuntuforums.org/showthread.php?t=1316126&page=4) suggests using backports-karmic, but I suspect that won't work on Lucid (it certainly won't let me install)

Another guide [https://help.ubuntu.com/community/AspireOne/110L](https://help.ubuntu.com/community/AspireOne/110L) suggests using madwifi, which was previously installed. I ran through the steps in order, but wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz) just returned the message "HTTP request sent, awaiting reposne... 403 Forbidden", so that seems unlikely to work either!

sudo ifconfig wlan0 up returns SIOCSIFFLAGS: Unknown error 132

sudo modprobe ath_pci returns FATAL: Module ath_pci not found

Obviously I am floundering around trying lots of different things! Can someone point me in the right direction please?!!

Thanks!

---

### Post by sandydoull on 2010-08-15
did you ever find a solution to this problem, currently having the same problem oin my aa1 with ubuntu 10.04 installed, i turned the wireless off with the hardware switch and now my wireless is greyed out no matter how much i try switchin ghte wirless on again!

---

### Post by Kerubu on 2010-08-15
Is this relevant? :

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454")

---

### Post by sandydoull on 2010-08-15
No, this is a harware issue specific to the aa1, when I turned off wireless with the netbooks own switch I was unable to turn it back on in the same way, I think for some reason you have to be root to turn the wireless on but not off, not sure but in any case I solved the problem by holding the wireless switch in the ON position during startup the entire time until the desktop has loaded, and presto my wireless was working again!

> **Kerubu said:**
> Is this relevant? :

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454)

---

