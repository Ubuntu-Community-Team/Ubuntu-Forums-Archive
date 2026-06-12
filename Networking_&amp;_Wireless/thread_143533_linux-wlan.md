---
title: "linux-wlan"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by heislord5 on 2006-03-12
I can't get this working.

1) Using synaptic package manager installed the package.
2) Went to system->administration->networking
3) Saw wlan0 there.  Configured WEP, open, put in secret key from modem/router, chose ascii (is that the correct choice?), gave the correct SSID for my network.
4) It said active (it says that even when I intentionally enter wrong configuration data)
5) Went to firefox and no connection.  Should firefox be set to direct connection or automatically detect?
6) Go back to networking and wlan0 disappeared.

help!  DWL-122 Dlink wireless usb is supposed to work with this.

---

### Post by Jason_25 on 2006-03-12
```

sudo iwconfig

```
should tell you what's really going on.

---

### Post by heislord5 on 2006-03-12
lo         no wireless extensions
etho0    no wireless extensions
sit0       no wireless extensions

---

### Post by heislord5 on 2006-03-12
I rebooted and it shows modem.

But it has configuration that I can't change.  It is set to adhoc and I need it set to get available...(like my windows computer).  The configuration provided from the windowed environment is limited and does let me choose ad-hoc or whatever.  So is there a file somewhere that I need to edit?

---

