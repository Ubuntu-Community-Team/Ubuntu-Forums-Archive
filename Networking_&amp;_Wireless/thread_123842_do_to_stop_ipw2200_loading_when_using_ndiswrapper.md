---
title: "do to stop ipw2200 loading when using ndiswrapper"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by ajaustin on 2006-01-31
I have installed ndiswrapper as per the howto in the wiki and the windows drivers are installed and the ndiswrapper module loaded, but I also have ipw2200 module loaded still.

I can't find out how I can stop the ipw2200 module from loading.

Anyone know this?

Tony

---

### Post by Lambert on 2006-01-31
add to the file /etc/hotplug/blacklist

```
blacklist ipw2200
```

---

