---
title: "Aol Adsl"
date: 2005-03-18
forum: Networking &amp; Wireless
---

### Post by Lord C on 2005-03-18
I am helping a friend (via msn/phone) get his internet working.

He has AOL ADSL, via ethernet.
His router is all setup, and reserving him an IP via DHCP.

In Windows he used to have to change his MTU to 1400 in order for the Internet to work.

I can't find any info on AOL DSL / Changing MTU in Linux / Ubuntu.

I told him to sudo ifconfig eth1 mtu 1400, which I saw on google;
It didn't return any errors, just went to the below line.
I don't know if there is any commands before/after this - or how to restart the network.
All I know is this command didn't get the Internet working.

Any and all help is highly appreciated.

Thank you

---

### Post by alastair on 2005-03-18
Check the MTU value using "ifconfig" e.g.

ifconfig eth1 | grep -i mtu

---

### Post by Lord C on 2005-03-18
Thanks,

Now how do I actually change the MTU?

---

### Post by alastair on 2005-03-19
The command you did (ifconfig) MAY allow the MTU to be changed - check. If it does not work, perhaps the driver doesn't allow it (I don't know). Maybe a log message somewhere - or check google (or source for the driver).

NOTE - you /might/ not need to change MTU.

---

### Post by fat_larry on 2005-10-16
I'm an AOL employee and I can confirm that in the UK at least, you need to use an MTU of 1400 for best performance.  In Ubuntu for me this means ```
sudo ifconfig wlan0 mtu 1400
```, although I am yet to find the /etc/networking syntax for setting this value, ```
mtu 1400
``` doesn't do the trick...

---

