---
title: "Inspiron8600 ipw2100 wicd wext - works"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by inspiron8600 on 2009-06-22
Hi I thought id post up some config files on a inspiron8600 - works with
-----
NIC: PRO/Wireless LAN 2100 3B Mini PCI Adapter
Wireless manager: WICD 
WPA Supplicant driver: WEXT configured in wicd
WPA2 Preshared key TKIP+AES encryption on router (cisco netgear54xx)
-Router set to Not broadcast "after" initial setup

WICD config files (2) needed  - (one needs a one liner append)
------------
(1) after installing wicd 1.5.9
in directory /etc/wicd/encryption/templates/
you need to create a template file (1) 
- [which I named wpa2_hx]
-----
(2)
in directory /etc/wicd/encryption/templates/
you need to append name of said file in (1) into the file "Active" in the current directory
(I appended wpa2_hx)
-------------

 Other screenshots and files below should get you through the rest 


all material from here or wicd forums so thanks.

---

