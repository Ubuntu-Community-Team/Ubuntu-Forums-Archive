---
title: "wireless conected and working but notification area still displays &quot;!&quot;"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by maxxnitro88 on 2010-06-02
so i am about a week into using ubuntu.  installed it on an old hp laptop that i pieced back together, using a broadcom wireless chip set.  got all the drivers loaded and working, on any other network the notification area will display that it is connected no problem.  but on my home network it will connect to the wireless but the notification icon will still look like there is no connection.

something that may be useful to know is that i originally plugged the laptop into the the router via wire to download the wireless card drivers.

please help!


edit:

using 10.04 and gnome also...

---

### Post by maxxnitro88 on 2010-06-06
nobody?

---

### Post by Iowan on 2010-06-07
What's in */etc/network/interfaces* - should be only two lines defining "lo". Otherwise, you might edit */etc/NetworkManager/nm-system-settings.conf* - changing managed to "yes".

---

