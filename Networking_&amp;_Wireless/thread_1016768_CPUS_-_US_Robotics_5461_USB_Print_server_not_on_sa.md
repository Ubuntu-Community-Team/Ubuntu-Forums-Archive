---
title: "CPUS - US Robotics 5461 USB Print server not on same subnet"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by IQRules on 2008-12-20
US Robotics USR5461 has IP 192.168.2.1, 
printer is [http://192.168.1.1:1631/printers/My_Printer](http://192.168.1.1:1631/printers/My_Printer)
Ubuntu laptop has IP 192.168.1.100
Win Vista has IP 192.168.1.50

Vista can print, but not Ubuntu 8.10 laptop. Ping / surfing all work fine.

I did some search on CUPS setup, such as browsepoll.
Just can't figure it out.

Can someone help me out?

Thanks

---

### Post by Bujdee on 2009-01-31
I have the same problem.

On Windows Me, XP, Vista working fine.

On my laptop I use Ubuntu 8.04 but my printer HP 710C doesn't want to print.  

Here is a tutorial to set up CUPS, but this isn't working too...

[http://www.usr.com/support/5461/5461-files/printer_installation_linux/index.html](http://www.usr.com/support/5461/5461-files/printer_installation_linux/index.html)

Have you got the solution yet?

---

### Post by cheeseborough on 2009-04-15
I had the same problem with my USR 5461 with Intrepid. The cure for me was to upgrade the router firmware since doing that everything is OK.

The link to the firmware update is here:

[http://www.usr.com/support/product-template.asp?prod=5461]("http://www.usr.com/support/product-template.asp?prod=5461")

The version of firmware that did the trick for me is version 3.93.35.0.9; unfortunately it is described as "BETA".

---

