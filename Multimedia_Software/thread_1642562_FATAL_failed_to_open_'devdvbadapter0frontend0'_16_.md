---
title: "FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy"
date: 2010-12-10
forum: Multimedia Software
---

### Post by faris-uppercut on 2010-12-10
After alot of work I managed to get ubuntu to detect and use my dvb-s card, but when I can for channels I get issues:
```
sudo scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf

```output:
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

Im guessing this means that an application is already using the device but this is not true no other application is using it when i run lsof /dev/dvb/adapter0/frontend0 nothing is returned. Ive searched through google for a solution but cant find one, If anyone can point me in the right direction and help me get it working I will be for ever great full :).

---

### Post by faris-uppercut on 2010-12-11
Went to computer janitor cleaned everything, redid a scan and it works! so happy must have been an old package locking the card.

---

