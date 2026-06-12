---
title: "Remote print jobs accepted but don't print"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by reswob on 2011-12-27
This one is weird.

My house is networked.  The printer (HP1006) is connected to my machine (Ubuntu 11.10).  The printer is shared out to various other devices (Ubuntu 9.10, Windows XP, Windows 7 and OS X 10.4).  My son has been trying to print from the Ubuntu 9.10 machine.  Watching the print queue on my machine (11.10), I see the print job come in along with the pop up saying the job is processing.  Then the print job disappears from the queue and the popup says the print job is complete.  Except nothing has printed.

I've restarted the printer, restarted cups, re-downloaded the driver, printed from my machine and printed a test page from my machine.  But nothing.  

Anyone else seen this using HP or any other printer?

---

### Post by collisionystm on 2011-12-27
> **reswob said:**
> This one is weird.

My house is networked.  The printer (HP1006) is connected to my machine (Ubuntu 11.10).  The printer is shared out to various other devices (Ubuntu 9.10, Windows XP, Windows 7 and OS X 10.4).  My son has been trying to print from the Ubuntu 9.10 machine.  Watching the print queue on my machine (11.10), I see the print job come in along with the pop up saying the job is processing.  Then the print job disappears from the queue and the popup says the print job is complete.  Except nothing has printed.

I've restarted the printer, restarted cups, re-downloaded the driver, printed from my machine and printed a test page from my machine.  But nothing.  

Anyone else seen this using HP or any other printer?

Check your logs 

Look in /var/logs

---

### Post by reswob on 2011-12-28
Again, the logs say the print job was successful:

> localhost - - [27/Dec/2011:19:02:35 -0500] "POST / HTTP/1.1" 200 184 Renew-Subscription successful-ok
localhost - - [27/Dec/2011:19:56:21 -0500] "POST /printers/HP-LaserJet-P1006 HTTP/1.1" 200 374 Create-Job successful-ok
localhost - - [27/Dec/2011:19:56:21 -0500] "POST /printers/HP-LaserJet-P1006 HTTP/1.1" 200 423132 Send-Document successful-ok
localhost - - [27/Dec/2011:19:56:26 -0500] "POST / HTTP/1.1" 200 342 Create-Printer-Subscription successful-ok
localhost - - [27/Dec/2011:20:00:55 -0500] "POST / HTTP/1.1" 200 184 Renew-Subscription successful-ok
192.168.1.11 - - [27/Dec/2011:20:03:40 -0500] "POST /printers/HP-LaserJet-P1006 HTTP/1.1" 200 149484 Print-Job successful-ok
192.168.1.11 - - [27/Dec/2011:20:04:51 -0500] "POST /printers/HP-LaserJet-P1006 HTTP/1.1" 200 149484 Print-Job successful-ok
localhost - - [27/Dec/2011:20:05:42 -0500] "POST /admin/ HTTP/1.1" 401 163 Pause-Printer successful-ok
localhost - craig [27/Dec/2011:20:05:42 -0500] "POST /admin/ HTTP/1.1" 200 163 Pause-Printer successful-ok
localhost - - [27/Dec/2011:20:05:45 -0500] "POST /admin/ HTTP/1.1" 401 163 Resume-Printer successful-ok
localhost - craig [27/Dec/2011:20:05:45 -0500] "POST /admin/ HTTP/1.1" 200 163 Resume-Printer successful-ok
localhost - - [27/Dec/2011:20:07:24 -0500] "POST / HTTP/1.1" 401 244 CUPS-Get-Devices successful-ok
localhost - root [27/Dec/2011:20:07:24 -0500] "POST / HTTP/1.1" 200 1027 CUPS-Get-Devices -
192.168.1.11 - - [27/Dec/2011:20:08:40 -0500] "POST /printers/HP-LaserJet-P1006 HTTP/1.1" 200 149484 Print-Job successful-ok
localhost - - [27/Dec/2011:20:11:25 -0500] "POST /printers/HP-LaserJet-P1006 HTTP/1.1" 200 149252 Print-Job successful-ok
localhost - - [27/Dec/2011:20:59:15 -0500] "POST / HTTP/1.1" 200 184 Renew-Subscription successful-ok

The Renew-Subscription entries continue before and after.

You can see the remote print job 192.168.1.11 as successful and mine (craig) as successful, but only mine actually had printed paper come out.  The other, nothing.

The error log shows only the following for the time in question:

> E [27/Dec/2011:20:05:43 -0500] Failed to update TXT record for Hewlett-Packard HP LaserJet P1006 @ Joshua: -2
E [27/Dec/2011:20:05:45 -0500] Failed to update TXT record for Hewlett-Packard HP LaserJet P1006 @ Joshua: -2

The page log shows my name with the page in question, but not the remote user, implying that while the access log thought there was a successful print, the page log didn't.
> HP-LaserJet-P1006 craig 110 [27/Dec/2011:20:11:28 -0500] 1 1 - localhost hogback_waiver.pdf - -
HP-LaserJet-P1006 craig 110 [27/Dec/2011:20:11:28 -0500] 2 1 - localhost hogback_waiver.pdf - -

Any ideas?

---

### Post by collisionystm on 2011-12-28
does your sons computer have the correct driver loaded for the printer?

---

### Post by reswob on 2011-12-29
Yes, he has been able to print before no problem.  This just started happening within the last two weeks.

Outside of the normal updates from Ubuntu, there have been no changes to either computer.  I DID see an update to cups within the last week or so.

In case I didn't say it before, (or said it wrong), he's using 10.04 LTS.  

I will say that the most annoying thing about this setup is the fact that the other computers are hit or miss when it comes to using the printer.  Sometimes it works just great; other times, nothing.

Usually some sequence of the above mentioned steps fixes the problem, but not this time.  Think I should post over there?

---

### Post by collisionystm on 2011-12-29
> **reswob said:**
> Yes, he has been able to print before no problem.  This just started happening within the last two weeks.

Outside of the normal updates from Ubuntu, there have been no changes to either computer.  I DID see an update to cups within the last week or so.

In case I didn't say it before, (or said it wrong), he's using 10.04 LTS.  

I will say that the most annoying thing about this setup is the fact that the other computers are hit or miss when it comes to using the printer.  Sometimes it works just great; other times, nothing.

Usually some sequence of the above mentioned steps fixes the problem, but not this time.  Think I should post over there?


I am not sure how you set up your printer in 11.10, but gnome is still buggy with its new release.

I suggest you check / re-do your settings from the cups web interface on your computer.

[http://localhost:631/admin](http://localhost:631/admin)

---

