---
title: "Wireless Firmware Missing on Dell Inspiron B130"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by Atreideskid on 2011-02-09
Just switched to Ubuntu 10.10.  I'm unable to connect to wireless internet or Ethernet.  I don't know why the Ethernet connection is not working, but am not currently concerned with that.  

Wireless networks has red exclamation point and says "Device not Ready (Firmware Missing).  

In lscpi network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

I've read through a few threads, and have attempted to follow directions given others.  I am finding myself needing specific aid though as my responses to suggestions are different from those others give.  I am fairly new to Ubuntu, been using it for a year or so.  Any help would be greatly appreciated!  

Thanks!

---

### Post by matthewboh on 2011-02-09
This worked well for me [http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto) 

Heard that Broadcom just released Linux drivers, but couldn't find any for that chipset.

---

### Post by Atreideskid on 2011-02-09
I scanned the how to, but I don't know where to begin.  I can't get the Additional Driver to work because there is no internet connection.

---

### Post by matthewboh on 2011-02-09
Try this

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

---

### Post by Atreideskid on 2011-02-09
> **matthewboh said:**
> Try this

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

Thank you so much!  It worked perfectly!

---

