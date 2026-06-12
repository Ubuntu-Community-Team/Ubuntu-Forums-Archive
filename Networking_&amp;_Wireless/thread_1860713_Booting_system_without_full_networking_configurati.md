---
title: "Booting system without full networking configuration"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by ceidleigh on 2011-10-15
Upgraded to 11.1 and it booted 3 times.  I now get the message booting  system without full networking configuration. It then freezes and goes  no further.  I have to power down and try again but it will not go  beyond that message.  Don't know what to do.  I tried recovery but same  message, same result.

---

### Post by aliencam on 2011-10-15
I'm  in the same boat, the upgrade completed successfully, then later I did another apt-get upgrade, and when I clicked "reboot to complete updates" I get this notice.  The same thing happens if I try to boot it with an ethernet cable plugged in.

---

### Post by hmandmpsaunders on 2011-10-16
I had the same problem, but I read that the problem is a left over PID in /var/run/dbus. ctl-alt-F1 then cd /var/run/dbus then sudo rm pid then your password then reboot gets you to the login gui.  I haven't found how to permanently solve this but I hope this helps get you working again.

---

