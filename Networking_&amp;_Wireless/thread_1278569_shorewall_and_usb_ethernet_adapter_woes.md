---
title: "shorewall and usb ethernet adapter woes"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by headnoodle on 2009-09-29
I have setup my netbook as a router/firewall on my network using ubuntu server and have bought a usb network adapter for the second network connection.

My internal network card is connected to my broadband connection and my usb is setup as my internal network.  I have setup shorewall and all works fine, my computers have internet access, etc going through the netbook/router.  My problem is that when shorwall starts at bootup an error is appended to shorewall-init.log saying 

'ERROR: Interface eth1 must be up before Shorewall can start'

once the netbook has booted, I can manuall run /etc/init.d/shorewall restart and all works fine but it never works straight off from bootup

i have tried moving the startup sequence and placing shorewall at the end in /etc/rcS.d by changing the number after S to 99 in the file name but still to no avail.

This is really doing my head in and any help would be most welcome

Thanks.

Dean.

---

### Post by ajgreeny on 2009-09-29
Try using the sleep option in the command to start shorewall, ie ```
sleep 30; shorewall
``` which will mean that shorewall is not actually started for 30 seconds after the command is carried out.  That may be long enough for the network to be up and running.  There may well be other ways to sort this problem, but this seems potentially the easiest.  If you know how long it takes for the network to be up and running, you may be able to adjust the time input for the sleep option.

---

### Post by headnoodle on 2009-09-30
> **ajgreeny said:**
> Try using the sleep option in the command to start shorewall, ie ```
sleep 30; shorewall
``` which will mean that shorewall is not actually started for 30 seconds after the command is carried out.  That may be long enough for the network to be up and running.  There may well be other ways to sort this problem, but this seems potentially the easiest.  If you know how long it takes for the network to be up and running, you may be able to adjust the time input for the sleep option.

I tried putting the sleep command in the /etc/init.d/shorewall script and it did sleep for 30 seconds.  The error still occurs though.  I am guessing something loads after the scripts in rcS.d that brings my usb network interface up.

---

### Post by headnoodle on 2009-10-01
can anyone else can help me with this on?

---

