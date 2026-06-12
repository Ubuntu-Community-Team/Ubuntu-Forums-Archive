---
title: "Connecting to wired connection kills wireless connections"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by jflash on 2011-07-20
Just had an issue crop up where connecting to a wired network seems to stop wireless connections from getting an IP (happens on multiple networks both while the cable is plugged in and once it's been unplugged; also persists across reboots). Machine is a Dell Latitude 2120n with UnionFS running. Connection was working fine prior to the wired connection.

Any ideas?

---

### Post by walt.smith1960 on 2011-07-20
Probably normal behavior.  Wireless won't connect while there is a wired connection, wired has priority

---

### Post by jflash on 2011-07-20
Thanks for the quick reply. I know wired has priority, but the issue is that this continues even after the wired connection has been disconnected (and after the system has been rebooted).

---

### Post by thefasterblueone on 2011-07-20
Be sure that wireless is set to "autowlan0" or something similar. And also to automatically connect on network connection loss.

---

