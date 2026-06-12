---
title: "Acer 5100, Wireless and Brother MFC-8720N Network Printer"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by denverstever on 2010-04-08
I'm pretty new to Ubuntu, but not a complete novice to Unix.  I used to do some light sysadmin on solaris servers when I worked in telecom.

Anyway, I finally got sick of Vista thrashing my hard disk constantly and decided to fire Bill Gates from my laptop once and for all.  Created an iso image of Ubuntu 9.10 set about installing on my Acer 5100 laptop (after backing up important files to dvd).

The install went pretty well with just a couple of things I'd like to mention here in case anyone else had these two problems.

1.  I was unable to log into my Verizon Westell wireless router using 64 bit WEP.  This turned out to be because version 9.10 defaults to 128 bit encryption.  After a google search, I found a suggestion to install a program called WICD, and it worked perfectly.  
Once installed, I set it to 64 bit WEP and getting on my local wireless went just fine.

2.  The second problem is that I wrestled with my Brother MFC-8720N network printer for a couple of days until finally getting it working.  The Printing utility under System Administration seemed to work, and the printer looked to be installed correctly.  BUT, no output would come out of the printer even though it always would appear just fine from the user interface when trying to print a document.

After another search for solutions, I finally ran across a smart comment from a guy who said that almost all printers will work using port 9100 and the HP Jetdirect Protocol.
It tried that with the Printer management utility, and it is now working great.

fyi, my Device URI is:  socket://192.168.1.11:9100   (where the ip address would be replaced with your printer's ip address)

Perhaps this will help someone.  As soon as I started using the jetdirect protocol and the device URI as above, the printer came to life.

VISTA IS DEAD NOW FOR ME !!   Ha ha... 

AND, the best part is that my hard disk is so quiet now running Ubuntu... absolutely incredible.  This laptop has never performed so well.

Good luck to all !!

---

