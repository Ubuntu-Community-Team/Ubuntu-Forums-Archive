---
title: "Wireless Problems since updates - WPA, NM and Ndiswrapper"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by Duncb on 2006-06-20
Hey all

I had my netgear wg511 working perfectly in dapper with WPA, ndiswrapper and network manager. However after the big batch of updates recently its broken.

I rebuilt the ndiswrapper modules for the new kernel, so thats not the problem.

Whenever network manager tries to connect, i get these error messages:

Jun 16 10:43:04 Morglum kernel: [17179679.632000] ndiswrapper (set_scan:1222): scanning failed (C0000001)
Jun 16 10:43:18 Morglum dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

Anyone got any ideas, this is driving me crazy..

---

