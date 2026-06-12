---
title: "how to find MAC Address"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by CrHaRcIzS on 2009-09-15
how do you find out what the MAC Address for the wireless internet is??

---

### Post by amauk on 2009-09-15
```
ifconfig
```
You're looking for the "HWaddr" entry

---

### Post by Iowan on 2009-09-15
**ifconfig -a** should all available interfaces - even if down. 
**lshw -C network** should also work, but it takes a bit more digging to find.

---

### Post by Zordkhan on 2010-01-09
My experience (2 days) teaches me that in the latest version (9.10) the command ifconfig gives me no information about the wireless adapter. For that, I had to use iwconfig, but that doesnt tell me the MAC address.

---

### Post by Vaphell on 2010-01-09
try **hwinfo --wlan**

---

### Post by s.fox on 2010-01-09
> **Zordkhan said:**
> My experience (2 days) teaches me that in the latest version (9.10) the command ifconfig gives me no information about the wireless adapter. For that, I had to use iwconfig, but that doesnt tell me the MAC address.

Hello,

Have you tried:

```
ifconfig | grep HWaddr
```

---

### Post by odysseusjak on 2010-01-09
Right click on the network connection in the panel and select 'Connection Information'.  The second line, 'Hardware Address' shows you the MAC address.

---

### Post by sgosnell on 2010-01-09
That gives you the MAC address of your computer, not the access point.  iwconfig in a terminal will give you the address of the access point.

---

### Post by Iowan on 2010-01-09
> **CrHaRcIzS said:**
> how do you find out what the MAC Address for the [COLOR="Red"]wireless internet[/COLOR] is??
I suppose it's worth asking which MAC address you seek - the wireless adapter (in your computer) or the access point?

---

