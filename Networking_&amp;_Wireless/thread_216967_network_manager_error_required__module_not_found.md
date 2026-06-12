---
title: "network manager error: required  module not found"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by syxbit on 2006-07-16
i had a dell e1505, and to get my ipw 3945 to work all i had to do was install the network manager.
i bought a different laptop (Asus A8Jm) which also has an ipw3945, but after installing network manager and rebooting i get the following error:
"Network Manager applet is missing some required resources"
any ideas ?

---

### Post by cucisan on 2007-03-07
same here on a asus f3ja - core duo centrino.. with intel wlan

---

### Post by Fitzcarraldo on 2007-03-07
If you see the following error message: "The NetworkManager applet could not find some required resources. It cannot continue." try entering the following command:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

---

