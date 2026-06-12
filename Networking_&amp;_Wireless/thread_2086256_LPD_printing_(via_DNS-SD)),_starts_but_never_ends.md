---
title: "LPD printing (via DNS-SD)), starts but never ends"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by fx3000se on 2012-11-20
Hopefully I am posting to the right forum?

I just bought a cheap printserver [http://www.sin-hon.com/Products_ny.asp?id=143](http://www.sin-hon.com/Products_ny.asp?id=143) which, I guess, is the same as [http://www.win-star.com/eshop/goods.php?id=58](http://www.win-star.com/eshop/goods.php?id=58) ;)

Printing from Windows and MacOSX works perfectly.

Under Ubuntu (12.10) the printer (a Canon MP510) was detected (Canon MP510-830590 (Canon MP510-830590, 192.168.1.99)) and I was able to configure  it. The local URI assigned is:
dnssd://Canon%20MP510-830590._printer._tcp.local/

Unfortunately printing does not work as expected. When a job is launched (no matter "Test Page" or a real doc) the printer starts to print but never ends (after 10minutes I usually give up ;) ).

The IP of the printserver is static (see above).

What (else) can I try?

Thanks for your help
Clemens

---

### Post by pdc on 2012-11-20
you might like to work your way through this ubuntu advice

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

I am not clear if you have the appropriate driver installed for the MP510; I would have thought if you could demonstrate the printer worked via a USB cable, you could then progress to resolving any network connection

---

### Post by fx3000se on 2012-11-21
thanks for your advice!
the "bug" is filed -> [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1081722](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1081722)

Regards
Clemens

---

