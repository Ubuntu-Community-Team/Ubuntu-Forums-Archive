---
title: "Not authorized to control networking in SSH console"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by spazzeri on 2010-11-24
Hello,

I want to control Network manager from the command-line. This worked well enough in Ubuntu 10.04 (with cnetworkmanager).

Since the upgrade to Ubuntu 10.10 however, a DBus exception is raised when I attempt to activate a connection from within a **SSH terminal**: 
```
org.freedesktop.NetworkManager.PermissionDenied: Not authorized to control networking.
```

---

