---
title: "Internet connection failing with VNC"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by Repabil on 2009-03-16
Hey

I've got problems with the internet connection from my stationary computer failing a while after being connected to via VNC (it's the only connection to the problem I've discovered). I'm able to fix the problem with ```
sudo dhclient eth1
``` however the connection usually breaks again after an hour or so. My stationary's setup is that eth1 connects to internet and is set to auto, eth0 is set to a manually set internal IP (which I VNC through).

---

### Post by khelben1979 on 2009-03-16
Have you tried using different VNC clients? [TightVNC]("http://en.wikipedia.org/wiki/Tightvnc") is a good client.

---

### Post by Repabil on 2009-03-16
You sure it's due to VNC? Because I connect to internally to the computer on eth0 and the failing internet is for eth1.

---

### Post by khelben1979 on 2009-03-16
No, I'm not sure it has anything to do with VNC.

I think that the timeout which is set by the dhclient is the real problem in this case. Try this:
```
sudo dhclient restart
```
when the network connection ends.

---

### Post by Repabil on 2009-03-17
> **khelben1979 said:**
> ```
sudo dhclient restart
```
```
SIOCSIFADDR: No such device
restart: ERROR while getting interface flags: No such device
restart: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```
I think that command only takes network devices as arguments.

---

### Post by khelben1979 on 2009-03-17
Sorry about that. In Debian you have a networking script. If it exists at your Ubuntu system over there, try that instead:

```
cd /etc/init.d/
sh ./networking restart
```

Also
```
man dhclient
```
will give you some options on how to use the command if the above does not exist over there.

---

### Post by Repabil on 2009-03-18
```
 sudo /etc/init.d/networking restart
[sudo] password for repabil: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```

---

