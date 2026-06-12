---
title: "Saved wireless configurations"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by lpc921 on 2012-01-22
I'm running Gnome Ubuntu 11.10
How to I list the networks that automatic connect is enabled and disable them?
How do I list the networks that have saved password?

I can't see the list in NetworkManager when the network is not in range and I can't save the configuration when I don't have the password for that network. Is that saved in a file?

[SLOVED] Use the old Network Connections GUI. Run nm-connection-editor if you can't find it.

---

### Post by lpc921 on 2012-01-22
I have solved the problem myself.

First go to [NetworkManager's website]("http://projects.gnome.org/NetworkManager/developers/") and find the example script using DBus. I'm using the [list-connections.py]("http://cgit.freedesktop.org/NetworkManager/NetworkManager/tree/examples/python/list-connections.py"). It list all the connections you have and their passwords, etc. Adding the following script at the end of the for loop deletes the connection you want.
```

if s_con['id'] == "Name of connection":
         settings_connection.Delete()
```

---

### Post by Sergius14 on 2012-01-23
Try to open "Network Connections".

From there you can deleted saved WiFi connections, even those that you never connected but "tried" by mistake.

---

### Post by lpc921 on 2012-01-23
Thanks. I didn't know Network Connections is still there after unity came out. That makes it a lot easier!

---

