---
title: "Ethernet stopped working after hard reboot"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by kristianz on 2010-06-13
My computer wouldn't come out of sleep mode, so I had to shut it down improperly. Now there's no ethernet network connection. The NIC works as I can start the computer by wake-on-lan, but somehow Ubuntu no longer sets up a network connection on it.

The green light on the NIC is lit up and blinking. I have changed no settings. It used to get an IP address from the DHCP no problem, but ifconfig now only shows 127.0.0.1.

Any ideas what might have happened?

---

### Post by Iowan on 2010-06-13
I've seen [this]("http://ubuntuforums.org/showpost.php?p=9437658&postcount=2") recommendation in a couple of places.

---

### Post by kristianz on 2010-06-14
Yep, that worked. Cheers!

---

