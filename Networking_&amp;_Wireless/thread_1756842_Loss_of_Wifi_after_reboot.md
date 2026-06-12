---
title: "Loss of Wifi after reboot"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by kenerly on 2011-05-12
I have a Compaq Presario M2000 with a Broadcom BCM4306 wifi card with Ubuntu 11.04

I did the following commands and the wifi works perfect, but after reboot I have to run the commands again? Any ideas.

Thanks

```
~$ sudo apt-get install b43-fwcutter
```

```
~$ sudo apt-get install b43-fwcutter firmware-b43-installer
```

```
~$ sudo modprobe -r b43 ssb
~$ sudo modprobe b43
```

---

### Post by MasterNetra on 2011-05-12
> **kenerly said:**
> I have a Compaq Presario M2000 with a Broadcom BCM4306 wifi card with Ubuntu 11.04

I did the following commands and the wifi works perfect, but after reboot I have to run the commands again? Any ideas.

Thanks

```
~$ sudo apt-get install b43-fwcutter
```

```
~$ sudo apt-get install b43-fwcutter firmware-b43-installer
```

```
~$ sudo modprobe -r b43 ssb
~$ sudo modprobe b43
```

Yea switch to STA :P, though you will need to install maverick's version of bcmwl-kernel-source sense its broke in natty.

Driver:[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

Recommend locking it using synaptic to prevent accidental upgrade.

---

### Post by kenerly on 2011-05-12
I have all the packages on

Driver:[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

installed, I guess I need to know how to "activate" them?

---

### Post by josephmills on 2011-05-12
please see post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5) thanks

---

### Post by kenerly on 2011-05-13
Tried everything on post 44 to no avail. (Thanks BTW)

I'm still having to type

```
~$ sudo modprobe -r b43 ssb
~$ sudo modprobe b43
```

after every restart.

---

