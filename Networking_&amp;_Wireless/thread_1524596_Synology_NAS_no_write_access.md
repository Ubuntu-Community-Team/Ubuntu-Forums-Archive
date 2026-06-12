---
title: "Synology NAS no write access"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by dennus on 2010-07-05
After a clean install of Ubuntu 10.04 I'm having a problem with my Synology DS207+ NAS.

The NAS is setup in Ubuntu like so...

I made a mount ...  mkdir media/synology

in my fstab it is configured as

```
10.0.0.11:/volume1 /media/synology nfs rw,hard,intr 0 0
```

Now... I can read and download files to it... but DELETING them and adding a new directory doesn't work?

Any ideas anyone?

---

