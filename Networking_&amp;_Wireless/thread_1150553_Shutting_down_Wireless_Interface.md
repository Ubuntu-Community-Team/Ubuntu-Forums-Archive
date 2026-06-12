---
title: "Shutting down Wireless Interface"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by nmahadkar on 2009-05-06
I am trying to shutdown my internal wireless network interface and use one that I bought.  The one that came preinstalled installed is slow and not as good at picking up a signal.  How di Ishut off the old one? and how can I assign the new one a static UP?

---

### Post by mattgyver83 on 2009-05-08
do an ifconfig to determine which is your old, and which is your new adapter.

then you can do this

Lets say eth0 = internal wifi card and eth1 is a usb dongle, and you want to use the dongle.

sudo ifconfig eth0 down
that will drop the connection from the one device

sudo ifconfig eth1 up
that will up the other device.

Hope that helps.

---

