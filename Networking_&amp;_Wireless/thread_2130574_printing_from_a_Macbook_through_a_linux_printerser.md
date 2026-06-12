---
title: "printing from a Macbook through a linux printer/server"
date: 2013-03-29
forum: Networking &amp; Wireless
---

### Post by HippieDave on 2013-03-29
I have an HP 3030 LaserJet connected via USB to my Linux desktop running Ubuntu 12.10.  In the past, I have been able to print from my Macbook (OS10.6.8) over my wireless system, but somewhere along the line in upgrading Ubuntu, I have lost the connection.
The Macbook sees the printer, but will not print to it, generating the error message: "Network host 192:168.11.2 is busy; will retry in 30 sec."  Alternatively, I sometimes get error message: "Cannot connect to printer; will retry...."

I have checked to verify that I have CUPS loaded, and even loaded Samba.  But nothing works. 
The [http://Localhost:631](http://Localhost:631) site shows the printer as "located" at URL: ipp://192.168.11.4:631/printers/hp-LaserJet-3030, and "connected" at  ipp://192.168.11.2:631/printers/hp-LaserJet-3030.

Any thoughts?

---

### Post by tgalati4 on 2013-03-29
If you don't see any obvious errors in /var/log/cups then it's usually easier to completely delete the printer and create a new printer.  Sometimes the print queue gets messed up (not unlike Windows) and the only recourse is to delete it and create a new one.  After verifying that it prints OK in linux using an application, not simply a test print, then try to print from the Mac.  Make sure "Publish Printer" is selected from CUPS on the linux machine that is hosting the printer.

---

