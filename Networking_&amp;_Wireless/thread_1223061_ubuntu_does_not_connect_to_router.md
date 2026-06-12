---
title: "ubuntu does not connect to router"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by newubu41 on 2009-07-25
I have Windows XP and Ubuntu 9.04 loaded. I accessed my Netgear software and found the Mac address and Bssid. I can access the internet through Windows but then started Ubuntu and entered the Mac address and the Bssid. The icon spins and eventually indicated the connection was not made. I don't know where to go from here. I am very new to Ubuntu, so any good advice will be appreciated.

Thanks

---

### Post by Tiwaz44 on 2009-07-25
The same thing is happening for me, I have no idea what to do!!!

---

### Post by philcamlin on 2009-07-25
your on a hidden network right

unhide the network for a moment connect then rehide it after :)

thats what i did and it solved my issue :popcorn:

---

### Post by newubu41 on 2009-07-25
Network is not hidden.

---

### Post by superprash2003 on 2009-07-26
post output of
1)lshw -C network
2)iwconfig
3)sudo iwlist scanning

from the terminal

---

