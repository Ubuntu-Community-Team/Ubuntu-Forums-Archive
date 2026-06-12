---
title: "Haupp. WinTV - CX24123 error"
date: 2009-08-06
forum: Multimedia Software
---

### Post by ftirapelle on 2009-08-06
Hi

I have installed mythtv on this configuration:
Asus M3N78-VM GF8200 RGVSM
AMD Ath64 X2LV 3100BOX6000+ 1MB
Haupp. WinTV HVR-1100 -t/a PCI

But the Haupp. WinTV will not be found. Output of dmesg

```
...
[ 13.148649] DVB: registering new adapter (FlexCop Digital TV device)
[ 13.150240] b2c2-flexcop: MAC address = 00:d0:d7:0d:30:88
[ 13.150477] b2c2-flexcop: i2c master_xfer failed
[ 13.150803] b2c2-flexcop: i2c master_xfer failed
[ 13.150806] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)
[ 13.150807] CX24123: wrong demod revision: 87
...

```
Thanks for help
Digg this Post!Add Post to del.icio.usBookmark Post in TechnoratiFurl this Post!
Reply With Quote

---

### Post by mocha on 2009-08-07
You better check out the MythTV wiki and search for that card.  It might not be supported yet or you need to build a module.

---

### Post by HappyFeet on 2009-08-07
You will need the [cx88]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)") modules.

---

