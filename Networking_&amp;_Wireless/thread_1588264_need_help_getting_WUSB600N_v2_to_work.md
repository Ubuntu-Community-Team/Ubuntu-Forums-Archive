---
title: "need help getting WUSB600N v2 to work"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by Faith95 on 2010-10-04
I'm following this tutorial:
[http://ubuntuforums.org/showthread.php?t=1580657&highlight=WUSB600N](http://ubuntuforums.org/showthread.php?t=1580657&highlight=WUSB600N)

at step 3 all i get is "linksys" but i decided to continue with it anyway, but it didn't wotk :(

I'm running ubuntu 10.04 and i'm new-ish to linux :)

please help!!

---

### Post by beau6282 on 2010-10-07
Hi faith I was just wondering if you have had any luck?  I am having the same problem.  Trying different things I have managed to get the card to be detected but I think it is using the wrong driver now.

Just kinda tinkering with different things. So how goes it for you?

---

### Post by beau6282 on 2010-10-07
I finally got my card working. with the code below

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf sudo modprobe -rf rt2870sta sudo modprobe rt2870sta dmesg | egrep 'rt28|usb|Phy' iwconfig


hope this help you

---

