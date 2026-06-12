---
title: "Bluetooth Sockets only semi-functional"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by grid_bug on 2012-03-06
When I attempt to use the Sample RFCOMM server supplied [here]("http://code.google.com/p/pybluez/source/browse/trunk/examples/simple/rfcomm-server.py"), and its corresponding client, I cannot connect the client to the server (on Ubuntu).

After connecting, the client tosses a "Connection Reset by peer", and the server never receives a connection at all. However, if I have one of my ArchLinux boxen run the server, then the client has no issues connecting or sending data. 

A look at /var/log/syslog shows that bluetoothd is barfing on pnatd, which from my googling [seems]("http://maemo.org/community/maemo-developers/ofono/") to be something mobile phone specific.
The exact message is
```
bluetoothd[13812]: Unable to spawn pnatd: Failed to execute child process "/usr/bin/phonet-at" (No such file or directory)
```

Strangely, OBEX works fine both ways, without any whining about pnatd.
This seems to be something very stupid broken (probably with my config, since few others seem to have this issue).

---

### Post by opabecker on 2012-05-02
Have you had any luck resolving this?  I am having this problem too.

---

### Post by Selmi on 2012-05-07
maybe related?
[http://www.spinics.net/lists/linux-bluetooth/msg14289.html](http://www.spinics.net/lists/linux-bluetooth/msg14289.html)

---

