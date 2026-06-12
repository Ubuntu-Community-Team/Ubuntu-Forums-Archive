---
title: "Natty 11.04 Asus EeePC wifi needs kernel 2.6.39"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by keithpeter on 2011-10-04
Hello All

The question is at the bottom of this post...

I've dropped back from 11.10 beta to 11.04 now on my Asus EeePC 1000 netbook. This netbook uses the rt2800pci wifi driver. Relevant lspci lines are

```
01:00.0 Network controller: Ralink corp. RT2860
04:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
```

With the stock 2.6.38 kernel, I have very long latencies when loading web pages on my home wifi (wpa2) and on unsecured wifi in a local arts centre (won't even load the 'terms and conditions' page).

Found a bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763974](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763974)

Attempted to attach a ppa to allow upgrade to 2.6.39, but ppa was empty, see

[http://ubuntuforums.org/showthread.php?p=10938556](http://ubuntuforums.org/showthread.php?p=10938556)

Followed suggestions in that thread and downloaded the following debs

linux-headers-2.6.39-02063902_2.6.39-02063902.201106241148_all.deb
linux-headers-2.6.39-02063902-generic_2.6.39-02063902.201106241148_i386.deb
linux-image-2.6.39-02063902-generic_2.6.39-02063902.201106241148_i386.deb
module-init-tools_3.13-1ubuntu1_i386.deb

Installed the module-init-tools first, then the three kernel debs (latter three using sudo dpkg -i linux*.deb). Then issued a sudo update-grub and restarted.

Reward was responsive wifi again.

Now, my question. What do I do about kernel updates? Is there no backport linkage possible to 11.10?

---

