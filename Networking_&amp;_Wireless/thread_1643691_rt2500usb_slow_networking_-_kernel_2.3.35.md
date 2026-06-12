---
title: "rt2500usb slow networking - kernel 2.3.35"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by manovotny on 2010-12-12
I have got continuing issue with slow Internet connection through wireless device - MSI-6861 802.11g WiFi adapter - driver rt2500usb.

I recall that it started after updating to 10.10 release. Don't exactly know what kernel I have installed at that time when it started. What is weird that I had beta of 10.10 and wireless USB works like a charm - there was linux kernel 2.6.35-19.20.
After a few upgrades of system, now I have last version of all packages - kernel 2.6.35-23-generic.

I tried to diagnose my network and from WIFI router I have ping response:
about 200ms, from wireless device it is about 500ms, I get often timeout from HTTP connection. When I connect through ethernet cable it is the same like from router and HTTP trafic is good. For reference I tried to boot into Windows 7 and there my wireless USB key works quick as nearly ethernet cable - no significant difference.

I looked for bugs and forums, but it seems that nobody have similar issues with rt2500usb driver.
--------------------------------------------
$uname -a 
Linux kraken 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

---

