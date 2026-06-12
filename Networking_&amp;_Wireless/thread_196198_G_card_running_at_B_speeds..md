---
title: "G card running at B speeds."
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by crthomas on 2006-06-13
I finally got my wireless card working, but its only working at 11mbps.  Its a G card.  Broadcom with ndiswrapper.  The same setup worked in 5.10 at G speeds.    The router is in the same room.  Any ideas?

---

### Post by DarthMandeep on 2006-06-14
What does iwconfig say? If it shows you are connected at 11M, try using "iwconfig wlan0 rate 54M" to set the association rate higher. If you're using ndiswrapper, then you've probably made sure to blacklist the bcm43xx driver. If not, do so.

---

### Post by crthomas on 2006-06-14
sudo iwconfig eth1 rate 54M fixed the problem, but after a reboot, it goes back to 11.  other than a script, is there an easy way to keep that setting?

Also, I don't know how to blacklist the bcm43xx driver.

Thanks

---

### Post by noname101 on 2006-06-14
To black list bcm43xx add blacklist bcm43xx to /etc/modprobe.d/blacklist.
```
sudo gedit /etc/modprobe.d/blacklist
```
Try adding wireless-rate 54M to /etc/network/interfaces. 
Add it under the device example:
iface wlan0 inet dhcp
wireless-rate 54M

---

### Post by dracule on 2006-06-14
i had the same problem, thanks.

---

