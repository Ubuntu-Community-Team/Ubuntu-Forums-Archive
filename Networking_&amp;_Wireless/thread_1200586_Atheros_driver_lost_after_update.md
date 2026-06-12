---
title: "Atheros driver lost after update"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by hambos22 on 2009-06-30
Hello! Well i have a Compaq laptop with Ar5007G wifi adapter. So i install the latest madwifi snapshots. After kernel update i don't have anymore internet connection. How can i reload the previous modules? i don't want to install again the madwifi beacause i'm afraid that i will make it worst. I have ubuntu 8.04..

The steps i did for the madwifi installation was

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential


tar xvzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
```

and then i reboot. Wifi worked well. After kernel change not any more.

---

### Post by tad1073 on 2009-06-30
have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=934215](http://ubuntuforums.org/showthread.php?t=934215)

---

### Post by hambos22 on 2009-06-30
thanx for the quick response. I've read all this stuff. I just want to know how to reload Atheros module, no how to install it again.

---

### Post by hambos22 on 2009-06-30
If i install again the madwifi it would be a problem with the modules?

---

### Post by hambos22 on 2009-06-30
please answer me! in a little update will done and i don;t know what i must do!

---

