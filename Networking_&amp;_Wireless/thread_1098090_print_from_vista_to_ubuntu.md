---
title: "?print from vista to ubuntu"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by amurphy96822 on 2009-03-16
HI:  I am new to Ubuntu, so perhaps silly question. Print server is an old dual boot Dell that was working perfectly well under PCLinuxOS, but I installed Ubuntu 8.10 because I wanted to use "dropbox" which is basically a Nautilus type program. The printer is an HP Officetjet j5750 (all in one), and Ubuntu recognized both the printer and fax, no problem. I had some problem sharing the printer and publishing and finally got that.  Now to intall and print from my HP Pavillion laptop upstairs running Vista. "Add a printer">"network printer" shows both the printer and fax and installs the printer easily as "//Main2/Officejet-5700-series", and using the Microsoft Color Printer as driver, prints a test page. But nothing else prints from this computer, i.e. firefox, openoffice, adobe, etc..

There are many tips out there about using something like "http://Main2:631/printers/Office...", but that does not work on Vista.  If you type that in the space allowed, it also copies it in the lower line designated "port" and Vista fails to find the printer. What to do?  Thanks

---

### Post by JohnnyB98604 on 2009-03-22
I don't know how to do this either.  I'd really like to use the printer hooked up to my ubuntu machine on my Vostro laptop (running Vista Home Basic) but it's not liking me much at all.

There seems to be many vague references to this working around the forms but I'm having a tough time finding something that actually walks me straight through how to do it.

---

### Post by utanja on 2009-03-24
having a related problem....

here is the setup:
Laptop is HP on 192.168.0.4 running Vista Home Premium
Desktop on 192.168.0.6 running Ubuntu with cups and samba printer on USB:1
router is Dlink on 192.168.0.1 (default)

Printing works perfectly when printing from the desktop
Laptop sees the printer and also prints. however, the following error msg appear in the printer msg popup screen

Access denied, unable to connect

Since the printer prints this is perplexing,,,

---

### Post by amurphy96822 on 2009-03-31
Not sure exactly how I solved this but here is what I think I did; I downloaded a network browser from the repository called pynetwork; I then ran it; I noted it could not "see" my ubuntu print server, so I added it by entering the name of the server (Main2) and the IP. then it could "see" the server and everything seemed to clear up in linux to linux printing and that seemed to also clear up the Vista problem.  Go figure.

---

### Post by amurphy96822 on 2009-03-31
Another clue:  almost all the hints and procedures you will find in the forum refer to Windows XP;  they do not work in Vista; all I can say is when your Vista machine finally "sees" the ubuntu hooked printer, it will work; if it asks you for a printer driver, click "generic", then Microsoft Color Printer.  Good luck.

---

### Post by rintintin on 2009-04-07
Thank you!
You solved my "Access Denied Unable to Print" errors in Vista with the suggestion to install a generic microsoft printer driver instead of the HP LaserJet 1000 one to print to my Ubuntu print server...

---

### Post by freddo__1 on 2009-06-24
I'm having basically the same problem, i can see the printer, add it, vista says the drivers aren't on the server, so i tried using the proper HP driver for my printer, which installs fine, and i can print a test page perfectly, but if i try to look at the job queue the status up the top says "Access Denied, unable to connect".  And if i try to print from an App in vista, the print job goes through from the app, the print queue icon pops up in the taskbar, but says 0 jobs, and if you double click on it to open it, nothing happens!!
 
I read the above comments, and tried the generic driver, but i don't have the Microsoft Colour Printer in generic, or Microsoft.  I have a MS Publisher Colour Printer, which i tried, but no luck with that.
 
Is there a setting in the Samba conf file that i need to change??  do i need to set browsable = yes or something in the [print$] section?? 
 
I would try and mess with some settings, but don't have the SU password for the machine its on right now...

---

