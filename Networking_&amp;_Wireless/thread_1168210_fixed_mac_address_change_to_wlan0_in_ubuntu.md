---
title: "fixed mac address change to wlan0 in ubuntu?"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by MuffinMan123 on 2009-05-23
I know Mac address is burned to the network card, but I know the value can be changed within ubuntu settings.

I tried macchanger and the value is always reset each time I reboot my computer.
I tried interfaces but the wlan0 setting won't scan for available network anymore.

Is there a way to put the mac address settings inside a system initialization file somewhere so each time it starts up it changes the wlan0 mac address to the one I assigned to?

---

### Post by MuffinMan123 on 2009-05-25
bump.

---

### Post by deviant on 2009-05-25
To change the MAC address you will first have to bring down the interface:

*ifconfig eth0 down*

After that you will need to provide the new MAC:

*ifconfig eth0 ether hw MACADDRESS*

Then bring the interface back up:

*ifconfig eth0 up*

* replace eth0 and MACADDRESS with your own interface / mac address

LATER EDIT: you can create a scrip file to do this at boot time, and have it load via /etc/rc.local

---

### Post by MuffinMan123 on 2009-05-26
and how do I do a script that initializes my settings on bootup?

---

### Post by jakslev on 2009-05-29
Bump

---

### Post by MuffinMan123 on 2009-06-02
bump again

---

### Post by m.maga on 2010-05-22
I know it is pretty late, but there are some answers here [http://ubuntuforums.org/showthread.php?t=94891](http://ubuntuforums.org/showthread.php?t=94891)

---

### Post by spotted zebra on 2010-05-24
once changed how do you change it back?

---

