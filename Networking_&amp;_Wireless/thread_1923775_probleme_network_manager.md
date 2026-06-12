---
title: "probleme network manager"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by makrem on 2012-02-11
I installed ubuntu ltsp is I tried to configure the network interface for thin clients with ip 192.168.0.1 through the menu system / administration / network
but "network" does not exist
how I should proceed and thank you in advance

---

### Post by praseodym on 2012-02-11
Hello,

this is the tool "gnome-network-admin", not the network-manager. Do you want to connect via single DSL modem via PPPoE or a router/modem combination? Try the network-manager from terminal:

```
gksu nm-connection-editor
```

---

### Post by makrem on 2012-02-13
how I can install this package without internet connection, or I can download this tool, then I use a virtual machine as a server.

---

### Post by praseodym on 2012-02-13
Is it Ubuntu-Studio? It does not ship the NM because of latency disturbing with the realtime kernel?! Download the packages **network-manager** and **network-manager-gnome** from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them by double clicking

---

