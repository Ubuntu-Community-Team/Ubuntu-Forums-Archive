---
title: "Sudden wifi disconnects in 10.04"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by xeptf4 on 2010-12-02
Hi,
I have experienced sudden wifi disconnects. My laptop fails to reconnect even after repeated attempts. It is only after a reboot that I am able to connect to the wireless. Is there any solution to this?

---

### Post by uncaspi on 2010-12-02
Determine your wifi card using sudo ifconfig or sudo iwconfig and suppose it's wlan0 try this command from the terminal.

sudo iwconfig wlan0 txpower 20 power off sens -80



and see if it helps.

---

