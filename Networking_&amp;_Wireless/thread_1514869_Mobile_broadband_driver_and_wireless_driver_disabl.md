---
title: "Mobile broadband driver and wireless driver disable after rebooting ubuntu 9.04!"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by anirvana11 on 2010-06-21
Please help me with this problem, It has been haunting me for weeks and I haven't been able to fix it so far:
When I installed the wireless driver 43XX series on my laptop using a wired internet, I saw the wireless network for a while and after I rebooted my system, My kernel(31) got corrupted and I got error "kernel Panic (and some sync error)",Thus I started using an older kernel(14),Now When I install wireless driver or mobile broadband driver(wvdial), they get vanished after the reboot and my mobile device modem isn't detected.But they are installed in my system(as shown by synaptic package manager but doesn't seemt to work)
Please help me fix this problem.I desperately want to use mobile broadband.

---

### Post by alexfish on 2010-06-21
hi

May be able to help with mobile connection

reboot the computer without the device then connect it . I am assuming its a USB device as you have not stated which Type it is.

so from the terminal use these commands and post the results

Code:

lsusb

ls -al /dev/disk/by-id/usb*Mass_Storage*

ls -al /dev/serial/by-id/usb*

---

