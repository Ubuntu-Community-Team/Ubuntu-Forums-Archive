---
title: "Using VueScan with unsupported scanner"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by j_latteier on 2006-08-01
I am having trouble setting up my film scanner (Minolta DiMAGE Dual IV). This scanner is not supported by Sane but it will run on VueScan. I downloaded the demo version. I have modified usb bus and device permissions and provided vendor and product IDs to udev. And I can produce successful scans (occasionally), but the scanner inevitably hangs, sometimes during focus, sometimes before. It can never produce more than one scan before hanging. VueScan release notes suggest that timing out may be the problem and recommend setting an environment variable, CONFIG_USB_LONG_TIMEOUT=y. How is this done? Is this passed to the shell with an export command? I tried this and it didn't help. Other Linux users report using VueScan with this scanner succcessfully. Any suggestions?
j_latteier

---

### Post by Causer1984 on 2006-10-05
Sorry, can you please show how you got Ubunutu even to acknowledge the scanners existence? I can't even get that far!

Cheers

---

