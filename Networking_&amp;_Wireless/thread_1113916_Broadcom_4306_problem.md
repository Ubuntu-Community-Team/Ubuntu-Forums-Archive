---
title: "Broadcom 4306 problem"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by bobhawkes on 2009-04-02
Hi,

Still a bit new to Ubuntu. Been through all the threads I can find and I'm running out of ideas. I would welcome any help...

I have loaded Intrepid 8.10 onto an old Dell machine. Also fitted a British Telecom Voyager 1040 wireless card I had lying around - Broadcom 4306 chipset. Guess what? I can't get it to work.

lspci shows the card as Broadcom 4303 (rev 3)
ndiswarpper shows the bcmwl5 driver installed
ifconfig only shows the ethernet port
iwconfig reports "No wireless extension" for everything.
lshw -C network shows the card as UNCLAIMED

b43xx driver is blacklisted.

I am guessing the driver is the issue - I have read that I need the b43-legacy driver but I can't find that anywhere.

Any ideas anyone?

Thanks.

---

### Post by kryptikos on 2009-04-02
Your best bet is to use the b43-fwcutter firmware. It is in the repositories and can be installed with apt-get. 

Someone wrote a howto in the forums:
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear")

Some background if interested about the 43xx series on Linux: 

[http://bcm43xx.berlios.de/]("http://bcm43xx.berlios.de/")

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

---

