---
title: "Litecoin mining rig won't automatically connect to wlan when available"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by wintoys on 2013-05-03
Hi i have this problem with all my linuxes. After disconnecting from wlan it does not connect back, no matter what. However if i want to get connection back i must type "sudo iwconfig wlan0 essid Zyxel" to terminal. Could you guys provide me a script that does following (without asking passphrase):

When it notices wlan go down, it waits 10 sec and if it is still off it will make this command: "sudo iwconfig wlan0 essid Zyxel"
Then it waits another 60 sec and if connection is still down it will "sudo iwconfig wlan0 essid Zyxel" again (can you make it do it infinite times?)

If someone could do this, well you are lifesaver. Also this would be good change to me learn some bash coding ;)

---

