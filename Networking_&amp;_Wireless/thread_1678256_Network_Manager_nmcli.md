---
title: "Network Manager nmcli ?"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2011-01-30
I was wondering if there is a way to install nmcli on Ubuntu 10.04.  I have a special Interfaces file for use with two Ethernet interfaces and an dhcp server.  I also have a broadband connection that I sometimes use.  My network connections work, but the network-manager applet in the notification area disappears and I need a way to connect to my broadband connection via the command line.

:confused:

---

### Post by StiveKnoxx on 2011-02-07
You need the lastest netwotk-manager (0.8.1):
```
             sudo add-apt-repository ppa:network-manager/trunk  
sudo apt-get update && sudo apt-get upgrade
```

---

