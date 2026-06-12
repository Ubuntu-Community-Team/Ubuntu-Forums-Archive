---
title: "Unable to kill process that are interfering with program"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by nothreat33 on 2010-10-05
I"m trying to kill some processes that are interfering with airmon-ng

When I run airmon-ng and tell it to turn on monitor mode on a given interface it says:

```
Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
20875	wpa_supplicant
20879	NetworkManager
20883	dhclient
20965	avahi-daemon
20966	avahi-daemon
```

I then try to kill these by typing kill [PID] but they restart immediately. if kill and killall commands wont work how else can I turn these off?

EDIT: airmon-ng check kill 

kills these but they also still come back.

---

### Post by krishnandu.sarkar on 2010-10-05
kill -9 PID

---

### Post by nothreat33 on 2010-10-06
Thanks tried that but it didn't work either.

---

