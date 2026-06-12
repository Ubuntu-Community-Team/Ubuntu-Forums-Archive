---
title: "Networking Printers with Ubuntu 10.10 and 11.04"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by nicknefarious on 2011-05-22
To All,

I am trying to share an HP DeskJet F2288 All-in-One printer across a network from an Ubuntu Desktop to 2 laptops - one  Windows 7 the other Ubuntu 10.10 64-bit (both over a wireless network). 

The printer is USB connected to a desktop machine running Ubuntu 11.04 (32-bit). On this machine I have installed Samba and CUPS. I have followed the directions in this - [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") Ubuntu documentation and after doing this the shared printer with correct IP appeared in the Printing window on my Ubuntu 10.10 laptop. If I open **System > Administration > Printing** two printer icons appear. One of which is the same printer but for when it was set up directly connected by USB - it is currently not connected by USB so this printer icon does not have the tick to indicate it is ready and connected. The other printer icon is for the shared printer over the network and is labelled **F2200-series@192.168.1.100**. This printer has the ready and connected "Tick" on it. This IP address is the correct IP for the desktop that is USB-connected to the printer to be shared.

When I try to print something and select this printer the print job shows up on the Ubuntu laptop's Print Job Queue but never appears on the Print Job Queue of the desktop computer sharing the printer.

After some time showing the job as processing on my laptop it then indicates it is "Processing - Not connected?" and that's as far as it gets.

I have attached a screenshot of the job queue and job attributes windows open side by side. It shows an error in the job attributes window but when I search this I can't find anything specific to my situation.

As well as this I am also trying to connect another laptop to this printer over a wireless network (through the Ubuntu 11.04 desktop). To do this I installed Samba following the direction in this tutorial - [http://www.liberiangeek.net/2010/12/share-printer-ubuntu-10-0410-10-maverick-meerkat-windows-print/]("http://www.liberiangeek.net/2010/12/share-printer-ubuntu-10-0410-10-maverick-meerkat-windows-print/").

I tried setting up the WORKGROUP network on the Win7 Laptop and connecting to the printer from the Win7 laptop and had similar problems. The printer appeared on the Win7 machine and appeared to be connected and the Win7 laptop appears on the Ubuntu 10.10 desktop serving the printer but nothing would print. The job appeared locally on the Win7 laptop's Print Job Queue but never made it to the Ubuntu 10.10 Desktop (not anywhere I could see it anyway).

Please can someone offer me some help or a solution to this problem?

Regards,

Nick

---

### Post by nicknefarious on 2011-05-28
FUUbuntu...

Maybe I didn't provide enough information or detail for someone to help out?

---

### Post by JohnH on 2011-06-10
I hear your problem,

I now have the same or similar problem. I have happily connected a Samsung printer over a wireless network at home for quite a while but recently (after cups upgrade I think) I cannot maintain printer connection over network even thought it says it's ready. I have to reinstall the printer for each session. It's a pain in the rear.... 

I'm no expert so I can't help you but there may be a bug somewhere.

Regards
John

---

### Post by drdos2006 on 2011-06-11
There are numerous posts on being unable to connect Windows 7 to Ubuntu connected printers.
Windows has removed IPP ( Internet Printing Protocol ) in Windows 7, but XP can connect because IPP exists in XP
Windows 7 needs IIS on an Windows Server.
I have not been able to connect with Windows 7 even with MS patches. 
Use XP instead. 
If in doubt, use Firefox to connect to the IP of the computer with the attached printer in this manner:
http://<ip-address>:631 for information on installed printer. 
Google is your friend.

regards

---

