---
title: "Network configuration changes don't stick"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by pinkunicorn on 2009-03-19
I have a server running Ubuntu 8.04. Once properly started it works the way I want, but when it reboots it forgets all its network configuration and comes up with DHCP for eth0.

If I go to System -> Network Configuration and change to a static IP / netmask / default gateway and DNS servers it happily accepts that (after prompting for my password). However, on the next reboot everything is forgotten again.

Why doesn't these changes get saved anywhere? What file should I change to fix this permanently?

---

### Post by Iowan on 2009-03-20
8.04 *should* still be saving network configuration information in **/etc/network/interfaces**.

---

### Post by pinkunicorn on 2009-03-22
I see that I screwed up when writing the post: the server is running 8.10. There is still a /etc/network/interfaces file, but it only contains this:```
auto lo
iface lo inet loopback
```
There's nothing about eth0 at all. Since the interface is brought up at boot (although not the way I want), shouldn't there be a line in here?

---

### Post by trump1 on 2009-03-22
I'm having the same problem.
Anybody can help us?

---

### Post by Iowan on 2009-03-23
I don't have Intrepid, yet, so I don't know if the server version uses Network Manager.  Make a backup copy of your /etc/network/interfaces file, then edit in  your static settings (via **sudo nano /etc/network/interfaces** or **gksudo gedit /etc/network/interfaces**). Reboot or restart networking with **sudo /etc/init.d/networking restart**.

---

