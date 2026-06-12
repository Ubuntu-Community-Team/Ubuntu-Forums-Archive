---
title: "Wireless connection issues"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by onlineapps on 2009-11-03
When I turn on my computer, KDE won't connect automatically to my wireless network (WPA2 encrypted). It connects fine in Ubuntu and Xubuntu, but in Kubuntu, every time I reboot, I have to delete the connection and manually connect again. This happens whether or not I set it to automatically connect. Once I do the intial connection, it's fine... until I reboot.

Edit: IRC = win. Problem solved. Appended this line to /etc/network/interfaces:

```
auto wlan0
```

And everything works!

---

