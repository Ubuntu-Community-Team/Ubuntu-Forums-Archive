---
title: "Connect wireless automatically at startup"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by ale55andro on 2008-12-14
Hi, I'm not using GNOME (but am using GDM), which I know autoconnects to wireless with its network manager.

I was wondering if it's possible to modify certain config files, to get my wireless (eth1 - i know it works) to connect on either startup/login, before or at the same time as the wm (flwm).

This is an unprotected wireless network, too - I can connect it from the command line, but I need root permissions, and can't get it to do it automatically when I load up ubuntu.

Thanks in advance!

---

### Post by nixscripter on 2008-12-14
While it is probably possible by modifying config files, I would suggest writing an init script if you know exactly what you want to do.

If you write a script, and put it in **/etc/rc3.d**, it will be run when the computer enters run level 3 (when it's done with essential system services, but before loading the login stuff). Make sure to call it **S98something** to make sure that it will be loaded in the right order with other stuff.

Something like this should be close (don't just copy and paste, please):
```

#!/bin/sh

# My network startup script, thanks to the Ubuntu Forums
iwconfig eth1 essid "mynetwork" open
dhclient eth1
# end of script

```

Again, if you know what commands worked as root, use those instead.

Hope this helps.

---

