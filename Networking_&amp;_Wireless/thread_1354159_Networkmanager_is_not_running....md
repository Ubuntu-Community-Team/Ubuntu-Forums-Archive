---
title: "Networkmanager is not running..."
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by psyboy55 on 2009-12-13
I was upgrading to 9.10 when I restarted my computer... When I got back on it's only partially installed . The Internet isn't working and the network manager says "networkmanager is not running..." so now I can't finish the upgrade. When I type nm-applet into terminal it says that network manager is already taken. Error 1387.  Note: I have a wired connection.

---

### Post by Iowan on 2009-12-13
That sounds... inconvenient.
Have you tried configuring the interface via */etc/network/interfaces*?

---

### Post by psyboy55 on 2009-12-13
all it says is
```
auto lo
iface lo inet loopback
```

i want the interface eth1 to work (i think)

---

### Post by Iowan on 2009-12-13
That's what the file would look like for normal Network Manager-ed system. No guarantees for success, but using your preferred editor, either ```
sudo nano /etc/network/interfaces
``` or ```
gksudo gedit /etc/network/interfaces
``` and add the following:```
auto eth1
iface eth1 inet dhcp
```Save the file and reboot - hope for the best!

---

### Post by psyboy55 on 2009-12-13
Ahh it didnt work! this is so annoying! is there anyway i could update the system while its offline through usb or something? I have a ubuntu laptop could i bring files from there to my desktop?

---

### Post by preserve on 2010-01-23
There is a setting in the source (in my Jaunty network-manager) that does not agree with the /etc/init.d/NetworkManager startup script.

My loaded version is network-manager_0.7.1~rc4.1.cf199a964-0ubuntu2.deb

NetworkManager.c, line 55 reads:

#define NM_DEFAULT_PID_FILE     LOCALSTATEDIR"/run/NetworkManager.pid"

That puts the NetworkManager.pid file in /var/run

/etc/init.d/NetworkManager, line 28 reads

PIDDIR=${localstatedir}/run/NetworkManager

That puts the NetworkManager.pid file in /var/run/NetworkManager

To fix replace line 28 in /etc/init.d/NetworkManager with:

PIDDIR=${localstatedir}/run

Now it starts for me because the package can find the .pid file

Hope it works for you.

---

