---
title: "Ubuntu shutdown problem when connected to VPN"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by kounoupis on 2012-02-08
I have Ubuntu 11.10. Shutdown works fine in general. I noticed recently that if I try to shutdown while I am still connected to a VPN (I am using vpnc), then the shutdown process never completes, the laptop stays on, and I have to do a hard reset.

I found the following problem in kern.log:

[30892.467095] gnome-settings-[1886]: segfault at 7f99e529cef0 ip 00007f99e529cef0 sp 00007fff13574c08 error 14 in libdbusmenu-glib.so.4.0.5[7f99e6730000+17000]

---

