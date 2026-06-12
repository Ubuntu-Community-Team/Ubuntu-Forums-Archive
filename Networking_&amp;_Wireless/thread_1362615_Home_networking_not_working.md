---
title: "Home networking not working"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by KwaggarookDagga on 2009-12-23
HI
I have 1 laptop win7 1 PC mint 8 32bit and 1 PC ubuntu 9.10.
I have set up the shares and can ping all 3 device no problem. One day I can print share files between the lot and the next nothing. It is very anoying!!!.

I would have thought that between the ubuntu and mint machine it would b a doodle but no go...
I have configure samba and cups still no go WHY???

---

### Post by Morbius1 on 2009-12-23
I think we need more information about your setup.

(1) Where is the printer?
 - Attached to the Mint or Ubuntu box?
 - Or attached directly to the router?

(2) When you say you "configured samba and cups still no go"
 - Did you configure Samba to become the print server?
 - Or are you using the CUPS Server directly?

If the printer is attached to one of the linux boxes then please post the output of that box's smb.conf:

Open **Terminal**
Type **testparm -s**

---

