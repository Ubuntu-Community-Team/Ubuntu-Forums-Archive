---
title: "NetworkPrintingFromWinXP"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by Guns90 on 2009-03-09
Hello again everyone.  I'm trying to get printing done on a Vista/ubuntu 8.10 dual booted machine from a networked XP machine.  Everything works fine if I have the Vista/ubuntu machine booted up in vista; however, I can't get it working when its booted up in ubuntu. 

I followed instructions at [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) , but the 'Add Printer Wizard in XP won't accept the URL "http://garydesktop:631/printers/HP-Laserjet-P1006".  I verified that URL info at [http://gary-desktop:631/printers/](http://gary-desktop:631/printers/), so I'm stuck.  Can anyone help, please?

---

### Post by albandy on 2009-03-09
[http://gary-desktop:631/printers/printername](http://gary-desktop:631/printers/printername)

---

### Post by Guns90 on 2009-03-09
I've tried every variation I can think of.  No luck.

---

### Post by albandy on 2009-03-09
you can connect from firefox to [http://gary-desktop:631/printers/](http://gary-desktop:631/printers/) in the computer you are trying to install the network printer?

---

### Post by Guns90 on 2009-03-09
clicking on that link gets me 

		
Showing 1 of 1 printer.
  	Sort Descending 	 
HP-LaserJet-P1006 (Default Printer)
	Description: HP-LaserJet-P1006
Location: gary-desktop
Printer Driver: HP LaserJet P1006 Foomatic/foo2xqx (recommended)
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/HP_LaserJet_P1006?serial=AB0NF26

---

### Post by albandy on 2009-03-09
edit /etc/cups/cupsd.conf file
search for the string Listen localhost 631, and add Listen 0.0.0.0 9100
save and restart cups

then install the printer as a standard tcp/ip printer in windows

---

