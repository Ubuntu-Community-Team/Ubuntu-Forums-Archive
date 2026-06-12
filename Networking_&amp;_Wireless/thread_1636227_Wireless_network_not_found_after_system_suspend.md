---
title: "Wireless network not found after system suspend"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by elkingrey on 2010-12-02
Hello,

I have an AE1000 Linksys wireless adapter. It works great except one problem. When I suspend the computer and then come out of it, it fails to recognize the network on start up. The only way I can get it to recognize the network and connect is unplug it and then plug it back into the USB port. 

It recognizes the network fine on a full start up, but not off of a suspended session. Any ideas? Thanks!

---

### Post by chili555 on 2010-12-11
Here is a technique that often, but not always works. Open a terminal and do:```
sudo gedit /etc/pm/config.d/config
```A new, empty file will open. Add one line:```
SUSPEND_MODULES="rt3572sta"
```Proofread, save and close gedit. Now does it work?

**************
Note to searchers: Substitute your wireless driver module for rt3572sta above.

---

### Post by elkingrey on 2010-12-11
Nope. The problem persists. =(

---

### Post by ebeighe on 2010-12-30
i have a MSI wind U100, the wireless card is a ralink that i used to need to get a source package for rt2860 when using release 8.10, and that sortof worked.

Last week i tried out 10.10 and everything loaded up and worked, including the wireless, right away.
Unfortunately, every third or fourth time upon coming out of suspend, the wireless would get stuck and i would have to reboot to get wireless again. The wired network (and everything else, apparently) still worked fine.

I tried some of the suggestions here but gave up and tried 10.04.1 and there is much joy because that works well. I can suspend and unsuspend all day long and the wireless keeps working.

---

### Post by soldave on 2011-01-12
> **ebeighe said:**
> i have a MSI wind U100, the wireless card is a ralink that i used to need to get a source package for rt2860 when using release 8.10, and that sortof worked.

Last week i tried out 10.10 and everything loaded up and worked, including the wireless, right away.
Unfortunately, every third or fourth time upon coming out of suspend, the wireless would get stuck and i would have to reboot to get wireless again. The wired network (and everything else, apparently) still worked fine.

I tried some of the suggestions here but gave up and tried 10.04.1 and there is much joy because that works well. I can suspend and unsuspend all day long and the wireless keeps working.

I can confirm the same problem with my MSI Wind U100 using Ubuntu 10.10 Netbook Remix.  Coming out of suspend invariably leaves my wireless network unable to connect unless I reboot.

---

