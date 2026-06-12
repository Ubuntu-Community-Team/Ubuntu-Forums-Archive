---
title: "wlan0 interface down at boot"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by thinkmeta on 2009-07-09
I am looking for a way to set my wireless interface to be down at boot.  similar to a ifconfig wlan0 down.

i dont want it up after boot.

Thanks in advance.

---

### Post by kerry_s on 2009-07-09
i would just put the command in **/etc/rc.local**
that way it still gets configured.

---

