---
title: "Where are the settings of the network manager saved?"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by HotForLinux on 2013-01-29
I cannot find that info in the man pages, and I am puzzled because I am not asked for administrative passwords to change settings, but when I save my user home directory after changing the wireless settings and then restore it afer booting, the saved settings are not there.

---

### Post by steeldriver on 2013-01-29
AFAIK connections that are marked as 'Available to all users' get saved in 

```
/etc/NetworkManager/system-connections/*connectionname*
```including the key/passphrase (hence why the files are mode 600)

OTOH 'user-connections' get saved deep in the bowels of the home (~/.config ?) directory of whatever user created them

---

