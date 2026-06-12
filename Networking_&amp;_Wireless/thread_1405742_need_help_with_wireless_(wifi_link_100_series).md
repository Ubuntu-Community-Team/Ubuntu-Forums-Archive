---
title: "need help with wireless (wifi link 100 series)"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by sleekmountaincat on 2010-02-13
hi all,
moderately new to linux (but love it!). i am having some trouble though:
i have an acer aspire 1410 with an intel wifi link 100 series wireless card and an attansic device 1063 nic. neither of these are working at all. i am running crunchbang 9.04.01 linux kernel 2.6.28-13-generic. from my research, i need iwlagn and atl1e respectfully. both of these modules are present on my system but not loaded, after running modprobe though the devices still are not up and running.
any help would be GREATLY appreciated. thanks!

---

### Post by chili555 on 2010-02-13
Please open a terminal and do:```
sudo modprobe iwlagn
sudo modprobe acer-wmi
dmesg | grep iwl
lspci -nn | grep Network
```Please post the result and we'll be in a better position to proceed. Thanks.

---

