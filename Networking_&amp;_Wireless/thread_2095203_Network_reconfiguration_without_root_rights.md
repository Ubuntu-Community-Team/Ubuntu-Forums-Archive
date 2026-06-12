---
title: "Network reconfiguration without root rights"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by elmuchacho on 2012-12-16
Hello,

we sell Linux based instruments, and we would like to give to our customers the possibility to reconfigure the network interface (IP/DNS adress, DHCP) without giving them root access.

How should I do this ?
Is there a tool for this, or should I write scripts ?

Thank you

---

### Post by steeldriver on 2012-12-16
If you are using the network-manager service (the default for the current Ubuntu Desktop editions afaik) then ordinary users should be able to make changes via the regular nm-applet provided the connection is set up as a "user connection" rather than a "system connection"

[https://live.gnome.org/NetworkManagerConfiguration](https://live.gnome.org/NetworkManagerConfiguration)

---

