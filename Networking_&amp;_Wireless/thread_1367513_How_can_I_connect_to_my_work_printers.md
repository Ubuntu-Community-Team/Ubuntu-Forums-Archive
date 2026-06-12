---
title: "How can I connect to my work printers?"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-12-29
I work in IT support and there's about 4 network printers per school (7 schools in the district). I dual boot Kubuntu and XP Pro for different reasons but lately I've been sitting in Kubuntu for 100% of my time (gotta love that!). However, I can't seem to find our network printers on the network.

I was using both Dolphin and Konqueror to browse out to the path of smb://server (that the printers are connected to) to try and connect. I see all of the shares, files, folders, etc but no printers.

If I do the same thing on a windows computer, start - run - \\server, I see the shares, files, folders, AND printers.

What can I do to get hooked up to these printers? It's a Windows network, Windows server, Ricoh network printers. Laptop is Kubuntu Karmic 9.10 64 bit.

---

### Post by Fire_Chief on 2009-12-29
I would probably do direct IP mappings to the printers instead of going through the Windows Print server. Eliminates a dependency (server), does not require authentication to the domain before printing, and is faster to setup overall.

Cheers!

---

### Post by berksted on 2009-12-29
Not much documnetaion on printing to windows from ubuntu, but I did see a mention of some problems when the windows printer name is longer than 8 characters? 

[https://help.ubuntu.com/community/WindowsXPPrinter]("https://help.ubuntu.com/community/WindowsXPPrinter")

---

### Post by Roasted on 2009-12-29
I can add the printer based on IP, but I get a CUPS error when I try to do a test page - something about it being an unsupported format.

The printers we're using here are Ricoh Aficio's. They are configured with locked print - meaning when I go to the printer and select my last name in the que list, I can put in my 4 digit password and blam - all documents in the print que under my name pop out. 

I'm not seeing that option to add my login info in the driver, however I'm not positive it's really needed. Even still, I can't push a test print without an error.

I know when I set up this printer that it was using the SMB protocol in the configuration menu. I don't know if that's worth noting but I figured it was.

Any ideas?

---

### Post by Fire_Chief on 2009-12-30
There's another thread I found where a user had the same setup and how he solved it.
[http://ubuntuforums.org/showthread.php?t=1205601]("http://ubuntuforums.org/showthread.php?t=1205601")

Cheers!

---

