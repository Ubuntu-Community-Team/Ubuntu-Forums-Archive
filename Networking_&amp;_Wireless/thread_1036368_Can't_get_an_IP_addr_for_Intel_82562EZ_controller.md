---
title: "Can't get an IP addr for Intel 82562EZ controller"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by mr love and justice on 2009-01-10
Hi all,

I'm running 8.10 and can't get it to play nicely with my home network. My controller is an Intel 82562EZ, which I understand to be compatible with Ubuntu. Can't get it to connect via the GUI network manager, so I tried

sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

I get "No DCHPOFFERS recieved. No working leases in persistent database - sleeping."

I essentially have no idea what I'm doing. Getting good old eth0 an IP address would be nice.. Got some packages I feel like downloading. Is there any way this could be a problem with my Linksys switch? Seems absurd..

Thanks in advance

MLaJ

---

### Post by mr love and justice on 2009-01-10
A brief update: I added eth0 in /etc/iftab and set it up for dynamic IP address detection in /etc/network/interfaces (if I understand what I'm doing correctly..)

When I do this:

sudo ifup eth0

I still get the same result as before.

I have no idea what's going on..

---

### Post by mr love and justice on 2009-01-10
all of a sudden it works.. weird stuff. thanks for reading MLaJ

---

