---
title: "USB Wireless doesn't work when PL2303 USB-to-Serial is plugged in"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by seal1972 on 2011-05-01
Hi,

I'm running Ubuntu 10.04.2 LTS and I've got an USB wireless adapter, which works fine.
I want to connect to 4 serial ports via PL2303 USB-to-Serial cables.
When I connect these cables, all works fine; both wireless and serial ports are accessible... 

Until I reboot.
After that, I no longer have network connectivity.
lsusb before and after reboot is exactly the same, but the wireless adapter is no longer recognized by the system (WICD fails to detect a wireless network).

I had this setup running successfully for about a year, until last month I reinstalled Ubuntu.
The only change in the current setup is that I removed Network-Manager and installed WICD, so the wireless network becomes available to me before I login, allowing me to remote access the box and reboot it, etc.

I could use some suggestions how to troubleshoot this issue.

Cheers,

---

