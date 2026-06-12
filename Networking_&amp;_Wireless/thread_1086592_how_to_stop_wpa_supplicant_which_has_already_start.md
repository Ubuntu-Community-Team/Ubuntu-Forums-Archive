---
title: "how to stop wpa_supplicant which has already started in the background"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-04
Previously I run this command 
```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -B
```

Now I run it again and it said
```
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
```

how do I stop it?

---

### Post by kevdog on 2009-03-04
I believe the process is in the /var/run folder.  I can't remember for sure.

---

