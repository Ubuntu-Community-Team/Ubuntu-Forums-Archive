---
title: "[ask] how to NOT automate wireless at startup"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by freakyjohn101 on 2009-08-02
ht, i just finish installing xubuntu 9.04 and everytime i start xubuntu the wireless always automaticly started. Is there a way NOT to automate the wireless? in xubuntu 7.10 i can just disable network manager at startup and do the connection manually by typing ifconfig and iwconfig, but in 9.04 the wireless still turned on even after i disable network manager. is there a configuration files that i can edit to disable all wireless related automation system in xubuntu?

---

### Post by ajgreeny on 2009-08-02
If you right click on the "Network manager applet" in your notification area in the system tray, and choose "Edit Connections", highlight the connection you use and then deselect the auto connect it should do what you want, I think.

---

### Post by freakyjohn101 on 2009-08-02
nope... it still blinking... what i really want is that the wireless is not turned up at startup/booting the system.

---

### Post by martinbaselier on 2009-08-02
You could blacklist the kernel module for your wirelesscard, so it will only start if you manually load the module with modprobe.

Or, if you remove the networkmanager you can manually create connections in /etc/network/interfaces. Only the ones which are in the auto list will start automatically.

---

### Post by freakyjohn101 on 2009-08-03
thank's man it work... actually even after i remove the ath0 from auto it still blinking at boot time, but after i added new line "iface ath0 down" on interfaces file it work just the way i wanted.. thx...

---

