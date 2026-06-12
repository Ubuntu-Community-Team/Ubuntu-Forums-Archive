---
title: "network manager doesn't show up in notification area"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by killer62491 on 2010-06-08
hey all, im just getting the hang of ubuntu 9.10, and then all of a sudden 10.04 comes over and screws everything up with the upgrade. i did the upgrade, and now the network manager wont show up in notification areas... any clue as to why? help is greatly appreciated. also, my machine does register that the drivers for wireless card is installed, and when i run lshw -c net command with sudo priveleges, it says it can detect networks, so im confused as hell...
 
.::ALPHA::HECTOR::SIERRA::.

---

### Post by Iowan on 2010-06-08
You can see if it is actually running by checking (from a terminal) **ps -ef |grep nm-applet**

---

### Post by dkuhlman on 2010-06-08
> **killer62491 said:**
> hey all, im just getting the hang of ubuntu 9.10, and then all of a sudden 10.04 comes over and screws everything up with the upgrade. i did the upgrade, and now the network manager wont show up in notification areas... any clue as to why? help is greatly appreciated. also, my machine does register that the drivers for wireless card is installed, and when i run lshw -c net command with sudo priveleges, it says it can detect networks, so im confused as hell...
 
.::ALPHA::HECTOR::SIERRA::.

I fixed this after reading a suggestion in another thread.

Check in the the file /etc/NetworkManager/nm-system-settings.conf

If it says:

```
managed=false
```

then change it to:

```
managed=true
```

Hope this works for you, too.

---

### Post by wilee-nilee on 2010-06-08
Some of the panel applets seem problematic, the notification is one of them I just delete it and add it again from add to panel. I use only one panel and the window selector shows only half or a thin slice of the icon at times as well same method to fix.

Also if you want to edit that file you need to access by this.
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by killer62491 on 2010-06-08
> **wilee-nilee said:**
> Some of the panel applets seem problematic, the notification is one of them I just delete it and add it again from add to panel. I use only one panel and the window selector shows only half or a thin slice of the icon at times as well same method to fix.
 
Also if you want to edit that file you need to access by this.
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```
 
if i do this, will i need to run a command to activate/make it use the replaced file?

---

### Post by Iowan on 2010-06-08
> **killer62491 said:**
> if i do this, will i need to run a command to activate/make it use the replaced file?**sudo restart network-manager** *seemed* to work on my machine.

---

### Post by wilee-nilee on 2010-06-08
> **killer62491 said:**
> if i do this, will i need to run a command to activate/make it use the replaced file?

First I'm not sure this will fix the problem, so make sure you keep the gedit command to put it back if needed. Your only modifying 1 line not building a new script so just change the false to true hit save and it will do whatever voodoo that it do. ;)

I changed mine just out of curiosity.

---

### Post by wilee-nilee on 2010-06-08
> **Iowan said:**
> **sudo restart network-manager** *seemed* to work on my machine.

This makes the most sense.

---

### Post by zbyszek on 2010-06-10
Try install gnome-netstatus-applet, through synaptic or apt-get.

---

### Post by gsgleason on 2010-06-10
Mine starts up with a startup entry in system > preferences > startup applications.  The command is:
nm-applet --sm-disable

---

