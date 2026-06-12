---
title: "nm-applet libnm_glib_vpn.so missing"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by Eoghan Murray on 2009-01-22
Hi,

After upgrade to ubuntu 8.10 (which unhelpfully uninstalled the perfectly working wicd)  I find that the build in network manager can't be opened.

From running it from the command line I get an error about libnm_glib_vpn:

```
ldd 'which nm-applet' | grep vpn
libnm_glib_vpn.so.0 => not found

```

(replace single-quote with backtick in above)

How to remedy this without internet on the computer?

Thanks

---

