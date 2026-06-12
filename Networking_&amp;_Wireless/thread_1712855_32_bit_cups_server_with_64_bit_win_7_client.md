---
title: "32 bit cups server with 64 bit win 7 client"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by clskier on 2011-03-23
I'm running a CUPS print server using SAMBA on a Ubuntu 10.04 x32 bit  server.  The printer connected via USB is a HP LaserJet 4050.  It works  fine on all my networked computers (all 32 bit) including Ubuntu Netbook  10.10, Windows XP, and Windows 7.  I have recently added a new laptop  to the mix which came pre-installed with windows 7 x64 bit Home Premium.   I am pulling my hair out trying to get this thing to connect reliably  to my print server.

I started by adding a network printer.  Windows searched and found the  printer.  Great.  I added it.  It did not identify a driver, I selected a  generic printer, printed a test page, all was well.  Next time the  laptop went to sleep the connection to the printer was lost.  Deleting  the printer and adding again works, but only until the laptop goes to  sleep.  Also, I often have to search several times to find the printer.

I deleted the printer and added it manually using the IP address  identified in COPS web control panel.  Doing it this way adds the  printer, but a test print just gives me an error.

I have created a link manually using the "net use" command to map the  printer to LPT1.  This gave me an error 55.  If I use the find network  printers in windows until it finds the printer, then cancel, then map  using "net use", it worked.  But again, next time the laptop slept I  lost the connection.

Thinking this was a driver error, I connected the printer directly to  the laptop.  Windows identified it immediately, and I was able to  install the correct driver "HP LaserJet 4050 pcl5".  Repeated all the  above with the same results.

I notice that my CUPS install only has "HP LaserJet 4050 pcl3".  Can  this be an issue?  If so, how do I get the latest drivers for Ubuntu?

I'm thinking this is a 64 bit issue with an old printer, but it works if  I plug it directly into the laptop.  I can re-install 32 bit OS onto  the laptop, but that's a lot of work if all I need is a new driver for  Ubuntu.

---

