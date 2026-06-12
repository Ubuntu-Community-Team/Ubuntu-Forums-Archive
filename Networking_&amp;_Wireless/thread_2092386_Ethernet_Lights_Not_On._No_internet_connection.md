---
title: "Ethernet Lights Not On. No internet connection"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by jr_herman on 2012-12-07
Hello,

Its been a long time since I've since ive used ubuntu. 12.04 i believe. ):P Just installed 12.10. Mostly every is okay except I have no internet connection. Status lights on the ethernet port are not on at all. I've plugged in two ways on success. Modem->Router-> PC and Modem->PC. Below are my PC stats. What should I do?

Motherboard: MSI P67A
Ethernet port: 1 onboard

Also, I rember there being a new user thread that got you up to speed on everything you shuold do on a fresh install ie, third party drivers for video cards, sound, proprietary file formats, etc, etc. I'm looking for it is there one still around?

---

### Post by howefield on 2012-12-08
Thread moved to the "Networking & Wireless" forum.

---

### Post by s3a on 2012-12-08
Does your Internet work after running
```
sudo dhclient
```?

Edit: I read too quickly. Post the contents of
```
lspci
``` please.

---

