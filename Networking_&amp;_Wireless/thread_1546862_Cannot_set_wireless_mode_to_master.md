---
title: "Cannot set wireless mode to master"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by Jaken Veina on 2010-08-06
```

root@Atlantis:~# iwconfig wlan0 mode master
 Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
root@Atlantis:~# iwconfig wlan1 mode master
 Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.
```

All other modes except secondary work fine.

The wireless cards are both PCI, a Netgear WG311v1 and a Linksys WMP54Gv4.1, though I'm not sure which is which. Any thoughts?

---

### Post by linux18 on 2010-08-06
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode master

---

### Post by Jaken Veina on 2010-08-06
No dice.

---

### Post by linux18 on 2010-08-06
in that case your card might not support that mode

---

### Post by Jaken Veina on 2010-08-06
I'm not sure about the Linksys card, but the Netgear has been serving as an Access Point for months under pfSense, and I figure it's more likely that something's interfering with both cards than something is breaking the Netgear and the Linksys doesn't support master mode.

---

### Post by Thocrun on 2011-03-12
I ran into the same problem, just for reference I used [http://ubuntuforums.org/archive/index.php/t-844599.html](http://ubuntuforums.org/archive/index.php/t-844599.html) . To build from source.

Works fine atm. The only thing I noticed the ralink download link is different.

---

