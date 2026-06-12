---
title: "Ubuntu refusing WEP authentication"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by swenska on 2010-07-29
I've installed a Linksys WUSB300N adapter in 10.04LTS. The adapter successfully scans for networks and gets a signal, but when I attempt to connect to my network, the 10-character WEP key is apparently not accepted, as Network Manager pops back up again requesting authentication. I tried replacing Network Manager with wicd, but the problem persisted; wicd timed out while "Validating authentication." I've confirmed the key, and tried entering in lower- and uppercase. I don't control the router, so cannot switch to WPA or disable security. I had the very same problem with a correctly installed Linksys WUSB11 ver2.6. Any help for either of these models would be greatly appreciated.

---

### Post by marc.verwerft on 2010-07-30
Have a look at the log files:
- /var/log/syslog
- /var/log/messages
- /var/log/daemon.log

Use a regular editor to view them or 'System/Administration/Log file viewer' if you feel more comfortable with a GUI.

Regards,

Marc

---

### Post by swenska on 2010-08-03
Sorry for not responding earlier, my connection problems have been universal. I'm not sure why, but downgrading to Jaunty 9.04 fixed the problem with the WUSB11 adapter. The WUSB300N still fails to connect, but I've successfully established a connection. Thank you for your response.

---

