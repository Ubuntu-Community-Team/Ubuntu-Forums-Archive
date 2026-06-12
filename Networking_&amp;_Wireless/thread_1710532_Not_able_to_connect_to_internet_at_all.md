---
title: "Not able to connect to internet at all"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by koalaiberico on 2011-03-20
I've bought a new laptop "TOSHIBA SATELLITE L650", I installed Ubuntu 10.04, but I don't seem able to access my internet connection either wired or wiredless.  I reinstalled it again with the ethernet cable with the same result.  The funny thing is that on Windows 7 it works perfectly.  I wonder if anyone has a solution for this; in the meantime I'll keep using Windows although I don't really like it.  Nowadays, when you buy a new computer you have to put up with a Winsows installation whether you like it or not; at least here down under. 

Thank you

I seem to have found the solution for the problem.  What it was needed was the lan driver since this version of Ubuntu comer without that for the hardware installed on that laptop.  The driver is:
compat-wireless-2.6.38-3.tar.bz2.  Just install it.

---

### Post by dineshs on 2011-03-20
In a terminal (applications-accessories-terminal run ```
sudo lshw -C network
``` and post the result.The output will give you details about network hardware(something like [COLOR="Blue"]Atheros Communications AR8152 v1.1 Fast Ethernet[/COLOR]).Now search google for solved threads reg this hardware .

---

### Post by koalaiberico on 2011-03-22
I seem to have found the solution for the problem.  It was the  Lan driver which doesn't come with this version of Ubuntu for this particular laptop.  The driver is:
compat-wireless-2.6.38-3.tar.bz2.  Install it and there you go.

Cheers

---

### Post by koalaiberico on 2011-03-22
I seem to have found the solution for the problem.  It was the  Lan driver which doesn't come with this version of Ubuntu for this particular laptop.  The driver is:
compat-wireless-2.6.38-3.tar.bz2.  Install it and there you go.  You can find the driver at this address "http://linuxwireless.org/download/compat-wireless-2.6" and download the file above.  Good luck.

Cheers

---

