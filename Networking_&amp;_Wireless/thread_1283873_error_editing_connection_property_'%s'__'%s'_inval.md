---
title: "error editing connection: property '%s' / '%s' invalid: %d"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by TheMixtureMedia on 2009-10-06
Can someone help me with this error editing connection: property '%s' / '%s' invalid: %d I just did a update and this happened. I can not get on my wifi I am using my wifes computer for this. I reallly need back on can someone please help me error editing connection: property '%s' / '%s' invalid: %d

---

### Post by TheMixtureMedia on 2009-10-06
Anyone??

---

### Post by bogdan.veringioiu on 2009-10-06
Hi.

I ran into the exact error while trying karmic beta from usb boot.
I wanted to set up my dsl connection, and, when saving the settings, the error you mention popped up.
However, I managed to configure the connection (pppoe) using pppoeconf.
Probably hitting a bug in NetworkManager.
EDIT:
I actually found the bug, as I imagined:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/438771](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/438771)

They are stating here:
> This bug was fixed in the package network-manager - 0.8~a~git.20091005t192303.1d28ad1-0ubuntu1
Probably the fix will come with the updates...

Bogdan

---

