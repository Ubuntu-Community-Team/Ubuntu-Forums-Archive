---
title: "USB Network Adapter WNDA3200 Not recognised at boot"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by tydfil on 2012-02-17
Random behaviour at boot on my Optiplex 745.  Sometimes the device is recognised at start up and everything works fine.  Most times the device is not recognised during boot and it must be unplugged and plugged back in to work?  Once working it works fine.

I have included copies of the output of commands suggested in the sticky.
wlan shows output when it has worked at boot
nowlan shows output when it has not been recognised

I am running Ubuntu 11.04, 2.6.38-13-generic i686

---

### Post by praseodym on 2012-02-17
Force the module to load at startup

```
echo ath9k_htc | sudo tee -a /etc/modules
```
or setup an udev-rule (more elegant ;-) ):

```
gedit /etc/udev/rules.d/10_wlan_stick.rules 
```
Insert
```
# UDEV-Rule for NetGear ID 0846:9018
SUBSYSTEM=="usb", ATTR{idVendor}=="0846", ATTR{idProduct}=="9018", RUN+="/sbin/modprobe ath9k_htc"
```
Save, close, and restart UDEV:
```
sudo service udev reload
```

---

### Post by tydfil on 2012-02-17
Thank you so much.  Have used your more elegant solution and all is now as it should be.:D

---

### Post by boyofford on 2012-04-25
Hopefully this works for me as well.

I have the wnda3200 dongle and same problem (though I've been just putting up with it), but have just installed lubuntu on brothers PC which is using same dongle and he is less tolerant lol

---

