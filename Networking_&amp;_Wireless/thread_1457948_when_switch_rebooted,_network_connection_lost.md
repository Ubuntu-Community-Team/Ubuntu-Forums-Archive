---
title: "when switch rebooted, network connection lost"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by jdc on 2010-04-19
When there is a power failure at my university for about 30 minute, my computer stays up because of a UPS, but the switch it is connected to via ethernet is reset.  After this, my machine loses network connectivity until I manually select the network using nm-applet.

In System -> Preferences -> Network Connections, the network has the "Connect automatically" box checked.

However, in /etc/NetworkManager/nm-system-settings.conf, there is a line that says:

```
no-auto-default=00:30:48:b0:11:07,
```

and that is the MAC address of the ethernet card.

Could that line be the problem?

I'm running Ubuntu jaunty.

Thanks for any suggestions!

---

### Post by viralmeme on 2010-04-19
> **jdc said:**
> When there is a power failure at my university for about 30 minute, my computer stays up because of a UPS, but the switch it is connected to via ethernet is reset

You have to reacquire the connection, either manually or automatically, this might help.

[http://blog.mithis.net/archives/ideas/51-nm-autovpn](http://blog.mithis.net/archives/ideas/51-nm-autovpn)

---

### Post by jdc on 2010-04-19
> **ymitchell said:**
> You have to reacquire the connection, either manually or automatically, this might help.

[http://blog.mithis.net/archives/ideas/51-nm-autovpn](http://blog.mithis.net/archives/ideas/51-nm-autovpn)

There's no vpn in my set-up.  NetworkManager isn't automatically reconnecting to the wired network itself, and if I'm away from my office, that is a problem.

Any other suggestions?

---

### Post by viralmeme on 2010-04-19
> **jdc said:**
> Any other suggestions?

You could try and rejig the scripts for ifconfig ...

"Reconnect to the Network When Disconnected"

[http://twofoos.org/content/wpa_supplicant/](http://twofoos.org/content/wpa_supplicant/)

---

