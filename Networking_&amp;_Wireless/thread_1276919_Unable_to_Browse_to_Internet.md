---
title: "Unable to Browse to Internet"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by scottmc9 on 2009-09-27
I'm running 9.04 wirelessly and things were working fine until I upgraded the firmware on my wireless router. Every other wireless device on my network is working OK. The wireless connection on my XUbuntu machine is fine, but I caannot browse to any Internet sites so I believe it's a DNS issue. The browsers (Chromium and Firefox) indicate 'resolving hosts' for a long period of time and then come back with page cannot be displayed errors. I had been using DHCP. I tried changing the IP to manual and used my ISP's DNS server addresses manually as well. Even tried OPENDNS server addresses. Nothing seems to work. Then I deleted and re-created my wireless connection within Network Manager and the wireless connection is now re-established--but still cannot browse the Internet. What's up with this?
Caution: Linux is not my native tongue.

---

### Post by Iowan on 2009-09-27
Check contents of */etc/resolv.conf* to verify that it didn't get overwritten.

---

