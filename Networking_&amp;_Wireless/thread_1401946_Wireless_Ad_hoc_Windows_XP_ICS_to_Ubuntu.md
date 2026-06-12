---
title: "Wireless Ad hoc Windows XP ICS to Ubuntu"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by r123 on 2010-02-08
Dear Ubuntu-erers,

I am unsure how to go about getting Ubuntu to receive an ad-hoc wireless ICS enabled connection.

The internet connection is shared through a virtual machine running XP (with the USB wireless dongle under XP's control), on my desktop PC, in order to escape my ISP's no NAT policy. Ubuntu is on both the desktop PC (the sender), and the laptop (the receiver). The desktop and laptop also run windows 7.

I managed to get my laptop Ubuntu to connect to my virtual machine XP, by setting the IP, subnet and gateway of all wireless devices, as was suggested in [http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html) - I did use the Network Manager GUI, but pinging the desktop doesn't work.

Even with the IP configuration, Windows 7 on the laptop receives the internet fine. The next step is getting Ubuntu to receive. I can do any kind of configuration in a virtual machine, such as install Ubuntu.

In virtual machine XP I used 192.168.0.1 with subnet 255.255.255.0 and gateway 1.1.1.1. On the laptop Ubuntu 192.168.0.2 same everything else.

I understand nothing about networks. I know there is stuff I can do in the console, but how will Network Manager cope with me doing that?

Basically: Where do I begin learning?

---

### Post by r123 on 2010-02-12
Or simply please: Where can I learn about Ubuntu networking?

---

