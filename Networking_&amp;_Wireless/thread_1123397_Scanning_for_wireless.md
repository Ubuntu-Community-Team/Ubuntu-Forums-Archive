---
title: "Scanning for wireless ?"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by alket on 2009-04-12
In one Free Wireless zone, i dont know the connection name or any other detail, how can I sacan for wireless ?

---

### Post by chili555 on 2009-04-12
Open a terminal (Applications -> Accessories -> Terminal, if you are using Gnome) and type:```
sudo iwlist wlan0 scan
```Substitute your wireless interface, if it's not wlan0.

---

### Post by alket on 2009-04-12
Thank you, I scanned wlan0 but i can't connect :S
I take details of output and when i try to connect via Network Connections, it does nothing.

Im using Boradcom STA driver.

---

### Post by alket on 2009-04-12
please help, I need it urgently

---

### Post by chili555 on 2009-04-12
May I assume you are really trying to connect using Network Manager? Here is a guide on how to use it: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

