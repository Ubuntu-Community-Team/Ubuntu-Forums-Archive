---
title: "Broadcom Corporation BCM4311/ Ubuntu 8.10 / Dell Inspiron 1520 not working"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by pk_rulz on 2009-01-15
Hi

I just checked out the hardware support page [[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom]](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom]) and it shows that the given model has to be used with nsdiswrapper.

I had this device working great with Ubuntu 7.10. All I had to do was download the restricted driver and then it was "Out of the Box"

What I dont understand that 2 versions later why I cant use the same restricted driver and I have to use ndiswrapper ...

Please help ... 

Rgds
Pradeep

---

### Post by superprash2003 on 2009-01-15
well you could use restricted drivers.. under system->admin->hardware drivers

---

### Post by pk_rulz on 2009-01-16
I checked and it shows that it is already using wl driver .... just that it does not seem to work ... My Wifi LED also  does not glow

---

### Post by Ayuthia on 2009-01-16
> **pk_rulz said:**
> I checked and it shows that it is already using wl driver .... just that it does not seem to work ... My Wifi LED also  does not glow

Can you try the following to see if it will work (this is in the Terminal):
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```

---

### Post by pk_rulz on 2009-02-18
Sorry for the late reply

Did that ... Did not help much ... any more ideas

---

### Post by pk_rulz on 2009-02-19
Finally got the solution

The BCM4311 Wifi Card firmware needed an upgrade

Find the solution here
[http://ubuntuforums.org/showthread.php?t=1008072](http://ubuntuforums.org/showthread.php?t=1008072)

The above mentioned link refers to this site
[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

---

