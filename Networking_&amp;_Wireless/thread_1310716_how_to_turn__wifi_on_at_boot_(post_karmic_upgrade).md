---
title: "how to turn  wifi on at boot? (post karmic upgrade)"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by cybergalvez on 2009-11-02
Hi all, with intreped I had my wifi working so that the wireless network connected when the computer booted up, now since I upgraded to karmic, thats broken.  I checked the network interface file and everything is there, but the wifi only only connects when I log in.  Also now the network manager is registering that it is managing the connection, in the past it just showed that it was not managing the network connection.  How can I restore the previous behavior, I want the wireless working regardless of my login statsus
Thanks for any and all help

---

### Post by hal10000 on 2009-11-02
Use wicd instead of network-manager, it's much better or just remove network-manager from the startup process:
```
sudo sysv-rc-conf
```

---

### Post by cybergalvez on 2009-11-02
> **hal10000 said:**
> Use wicd instead of network-manager, it's much better or just remove network-manager from the startup process:
```
sudo sysv-rc-conf
```

Fantastic! that works great, easy to install, easy to use and it just works!
Thanks

---

