---
title: "internet connection is not enabled"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by Ubuntee1 on 2011-11-21
Hi,
I have recently installed Ubuntu 9.10.I already have internet connection which is working on windows7.
but on ubuntu the internet is not working. 
```
sudo vim.tiny /etc/network/interfaces 
```shows only below contents
auto lo
iface lo inet loopback
i have added IP, subnet and gateway addresses as available in windows but still network is not enabled.
Please help.
Regards,
Ubuntee

---

### Post by praseodym on 2011-11-21
Hi,

is it about LAN or wireless? The network-manager was buggy from that 9.10 CD, it needs to be updated. 

But: 9.10 is outdated, I recommend installing at least 10.04

---

### Post by Ubuntee1 on 2011-11-21
Hi ,
 As suggested i have downloaded ubuntu 10.04.03 from ubuntu site.
i have downloaded the iso file.
and i created the bootable usb drive by following the procedure mentioned there.
 
but i am  not able to boot from pendrive.
i have changed the boot priority also.
 
please help.

---

### Post by dandnsmith on 2011-11-22
If you are unable to boot from pendrive, presumably you installed 9.10 a different way (from CD?) - so try that instead.

---

