---
title: "Blueman GN and NAP can't connect"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by chugun on 2009-05-07
When i try to connect to GN or NAP service created from blueman ( 1.10 from Jaunty Ubuntu PPA) from windows and get error that say " can't connect"

in daemon.log 

```
May  6 21:44:08 mainws bluetoothd[30448]: link_key_request (sba=00:0B:0D:04:A7:4B, dba=00:22:69:FF:5C:32)
May  6 21:44:08 mainws bluetoothd[30448]: Hangup or error on BNEP socket
```

When i try to connect GN from Blueman to windows machine it's connect normal and bring up iface bnep0

What's can be wrong?

---

### Post by chugun on 2009-05-07
it's seems like bug in new versions.
it's work fine before upgrade some thing of that ( from blueman ppa)
```
bluetooth [4.32-0ubuntu4 -> 4.36-0ubuntu2]
bluez [4.32-0ubuntu4 -> 4.36-0ubuntu2]
bluez-alsa [4.32-0ubuntu4 -> 4.36-0ubuntu2]  
bluez-cups [4.32-0ubuntu4 -> 4.36-0ubuntu2]
bluez-gstreamer [4.32-0ubuntu4 -> 4.36-0ubuntu2]
bluez-utils [4.32-0ubuntu4 -> 4.36-0ubuntu2]
libbluetooth3 [4.32-0ubuntu4 -> 4.36-0ubuntu4.2]
``` or 4.32-0ubuntu4.1 versions

after upgrade i get an error

any one can confirm that?

---

