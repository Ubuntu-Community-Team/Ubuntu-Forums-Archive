---
title: "Wired network help"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Vicker3000 on 2009-01-06
My desktop is using 8.04 and my laptop is using 8.10.  I have the internet connected to my desktop through the motherboard's built in jack and then an ethernet cable running from the desktop to the laptop, using a network card.  For some reason the two computers aren't talking to each other.  

I have both eth0 and eth1 set to roaming mode in Network Manager on the desktop.  Plugging the internet cord into either jack on the desktop results in a working internet connection for the desktop, so both jacks seem to be functioning correctly.  Plugging the internet cord into the laptop also results in a working internet connection.

What am I doing wrong?  Please note that I'm still pretty new to Ubuntu.

---

### Post by superprash2003 on 2009-01-06
do you want your desktop to share internet connection with he laptop?? or just a network?? if its internet connection sharing then follow this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. if not just set static ip address for both the machines on the right interface card.. set the desktop to ip 192.168.0.1 ..a nd set the laptop to ip 192.168.0.2 with gateway as 192.168.0.1

---

### Post by Iowan on 2009-01-06
Is that a straight or crossover cable between the two machines? (should be a crossover cable).

---

