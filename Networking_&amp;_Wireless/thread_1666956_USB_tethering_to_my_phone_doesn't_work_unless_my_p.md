---
title: "USB tethering to my phone doesn't work unless my phone is plugged in during boot"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by legoman666 on 2011-01-14
It's installed as a mobile broadband connection. Only works if my phone is plugged in during boot, otherwise plugging in my phone does nothing. 
For example, I booted my netbook earlier today but my phone wasn't plugged in. Tethering did not work, it just acts as if it isn't present. I rebooted (with my phone still attached) and now tethering magically works.

Any ideas?

---

### Post by |{urse on 2011-01-14
Does the command
```
lsusb
```
show that the device is connected when you plug it in?

Also what is the make and model of the phone?

Also Also is it able to establish a connection as a bluetooth modem with your computer?

---

### Post by legoman666 on 2011-01-14
double post. slow-*** forums.

---

### Post by legoman666 on 2011-01-14
> **|{urse said:**
> Does the command
```
lsusb
```
show that the device is connected when you plug it in?

Also what is the make and model of the phone?

Also Also is it able to establish a connection as a bluetooth modem with your computer?

```
Bus 001 Device 004: ID 0421:01c8 Nokia Mobile Phones N900 (PC-Suite Mode)
```

Yes, it shows up but the network manager does not list mobile broadband as a possible connection until I reboot (with the phone plugged in).

The phone is a Nokia n900. No sorry, my netbook does not have bluetooth. I have a bluetooth dongle but it doesn't work Ubuntu.

Thanks for your help.

---

### Post by |{urse on 2011-01-14
Hm, thats a new one.. I don't usually just google for answers but I did come across this script that provides an "on-demand" connection.

Sorry for the late reply. 

> sudo apt-get install wvdial

Then follow this guide (looks easy enough, but i haven't tried it personally.. your mileage may vary)

[http://forums.internettablettalk.com/showthread.php?t=61529](http://forums.internettablettalk.com/showthread.php?t=61529)

---

### Post by legoman666 on 2011-01-18
> **|{urse said:**
> Hm, thats a new one.. I don't usually just google for answers but I did come across this script that provides an "on-demand" connection.

Sorry for the late reply. 



Then follow this guide (looks easy enough, but i haven't tried it personally.. your mileage may vary)

[http://forums.internettablettalk.com/showthread.php?t=61529](http://forums.internettablettalk.com/showthread.php?t=61529)

Thanks for replying. I tried what that guide suggested, but it still appears that my netbook does not want to tether unless my phone is plugged in during boot.


Here is the result of following the guide:
```
andrew@keira:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
andrew@keira:~$ 

```

Says the modem doesn't exist. Is there a way to manually mount it or something?

---

