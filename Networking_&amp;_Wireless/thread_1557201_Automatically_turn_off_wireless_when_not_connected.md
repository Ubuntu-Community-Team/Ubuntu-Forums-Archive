---
title: "Automatically turn off wireless when not connected"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by gabriele.puppis on 2010-08-20
Hi! That's my first post, asking for an help to improve this simple script (it is run automatically at startup -- after the login -- to turn off the wireless card in case it is not connected to any router -- this helps me to save some batteries).

```

sleep 20
ifconfig wlan0 | grep -q "inet addr:"
if [ $? != 0 ]; then
  dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false
fi

```PS. note that the script must disable the wireless but let the user enable it again from the GUI (e.g., the network connection manager) in case of need (so commands like "rfkill" or "ifdown" cannot be used).

It would be great to have in the future a general script that automatically disables bluethoot/wireless/etc if not used.

---

