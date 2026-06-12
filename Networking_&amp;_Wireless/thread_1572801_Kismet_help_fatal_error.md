---
title: "Kismet help: fatal error"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by vaportrail_123 on 2010-09-11
Well, I'm trying to use kismet on my new installation of 10.4, and I get the following error:
root@ninjatower:/# kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.
I currently have airmon-ng installed and have set my wlan0 to monitor mode.
help please?

---

### Post by chili555 on 2010-09-11
> Please read the README for more information about configuring Kismet.Please read:```
less /usr/share/doc/kismet/README.gz
```Especially see sections 9 and 12. Then edit /etc/kismet/kismet.conf to specify source= for your sources. Here is the relevant section of mine for example. Yours will depend on your wireless card and driver.> --- snip ---
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl3945,wlan0,Intel
--- snip ---

---

### Post by vaportrail_123 on 2010-09-11
i found that exact line in the readme and got it to work and instantly felt like a moron. thanks for the help lol

---

### Post by chili555 on 2010-09-11
Glad it's working! Have fun!

---

