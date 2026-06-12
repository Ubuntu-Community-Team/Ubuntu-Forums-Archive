---
title: "Where to find the network manager icon?"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by ranjithbiotech on 2009-06-24
Hi For edit the static Ip where to find the network manager icon? can u help me?

---

### Post by jhannah on 2009-06-24
If you don't see the NetworkManager icon (similar to the Windows networking icon) in the Gnome panel, you might not have it installed, try running the below commands:

```
sudo aptitude install network-manager network-manager-gnome
```

After that, start it up with the below command and restart X (keep in mind if you run this while X is running, it will log you out so be ready before running gdm restart):
```
/etc/init.d/NetworkManager restart && /etc/init.d/gdm restart
```

At that point, the icon should show up but if not, you can modify the settings by clicking 'System' -> 'Preferences' -> 'Network Connections'

Hope that helps

---

