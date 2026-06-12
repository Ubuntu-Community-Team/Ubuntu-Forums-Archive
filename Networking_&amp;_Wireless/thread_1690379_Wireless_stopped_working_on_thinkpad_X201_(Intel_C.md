---
title: "Wireless stopped working on thinkpad X201 (Intel Centrino 1000 N)"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by jcline on 2011-02-18
I have Ubuntu 10.10 on a thinkpad X201.  Wireless was working, but has stopped.  It still works in windows, so it is not a hardware problem.  iwlist wlan0 scan sees the available networks, but I cannot associate with any of them, including my own.

Last night was my first attempt to connect to a secured network, and nm-applet failed to make the connection even after entering the WEP encryption key and SSID.  By turning networking off in nm-applet I was able to manually bring up the connection by editing /etc/network/interfaces and using ifup wlan0. (nm-applet seemed to be interfering as long as networking was turned on there.)  Wireless was working perfectly until I rebooted.  Now I can't get it to work at all.  (There were some partially completed security updates which completed when I rebooted.  I hope this wasn't the cause of the breakdown.)

I notice that wpa_supplicant is always running.  I tried killing it in case it might be interfering with the connection process, but something keeps restarting it.   Perhaps there is some wpa_supplicant configuration that has to be done to connect to a secure network?  

This is extremely frustrating, any help will be appreciated.

---

### Post by jcline on 2011-02-18
In fact the output from iwlist scan is variable.  After a few tries to restart the
connection, it gives no scan results.

I have just installed wcid in place of nm-applet, and am able to use the wireless again.
I would like to know why wcid works but nm-applet doesn't, and why manually using ifup with /etc/network/interfaces doesn't work.

---

