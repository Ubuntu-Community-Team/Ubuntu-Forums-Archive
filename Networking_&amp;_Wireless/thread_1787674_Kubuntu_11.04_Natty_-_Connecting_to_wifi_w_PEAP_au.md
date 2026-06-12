---
title: "Kubuntu 11.04 Natty - Connecting to wifi w/ PEAP auth (MSCHAPv2) drops"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by ksugihara on 2011-06-21
I am trying to connect to my wifi at work; it is WPA2 Enterprise w/ PEAP auth, and uses my active directory creds to authenticate.

The connection is somewhat slow but eventually works. But then network speed is incredibly slow, like maxing at 900bytes/sec. Then the connection will drop constantly.

I had my domain admin setup a WEP wifi spot for testing, and I can connect with no issues and browse fine.

Is anyone aware of a known issue or a possible fix for this? If you need more info, please let me know and I'll post it.

Wifi chipset:
Atheros AR5b97

---

### Post by ksugihara on 2011-06-21
bump

---

### Post by ario on 2011-10-09
Although when changing encryption to WEP it works better, I think it can be a problem with the driver of your wireless. Check results by trying Proprietary or Open-Source driver.

---

