---
title: "udev script for wireless making sure its correct"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by rawrmonster on 2011-10-29
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="rtl8187", ATTR{address}=="00:C0:CA:46:A3:5B", ATTR{type}=="1", NAME="wlan0" RUN+="/path/to/script"

i have been working on trying to build a udev script for a wile now and think i might have it right but would like to check before i plug it in ty in advance

---

