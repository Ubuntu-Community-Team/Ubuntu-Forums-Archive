---
title: "How to add Network Printer connected via router?"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by arun.in on 2010-10-25
Hi,

We have 3 computers with windows xp installed and two canon ir2200-ir3300 printer all connected through a router box. Each computer and each printer has ip addresses. It was configured like tcp ip enabled printer inside the local printer option. Each windows system can see both printer with ip and can select them to print.

Now we want to try ubuntu in **one of the system**. Couldn't detect the printer inside the ubuntu.

We have downloaded linux driver for the printer from the canon site. but found no documentation, so we tried to install it by typing ./setup in the folder and it started to install, finally a gui opened up to setup the printer, we gave the ip of the printer as 192.168.1.5 as we do in windows. and gui part has completed.

Now we can see the name of printer ( which we have typed in graphical setup dialog box earlier ) in System > Admin.. > Print..

It shows a warning sign over the name of the printer icon. and when we try to connect it shows the message connecting to printer, but the message in print job dialog box is processing and it remains so, for long time without printing the test page.

We didn't do any network configuration in ubuntu other than giving a manual ip and subnet mask as 192.168.1.3 and 255.255.255.0 in "Wired" tab ( auto etho ) in Network Manager and the icon shows connection.

Please help us. :(

---

### Post by dhyan on 2010-10-26
Hi Arun,

In My company we are using CANON-MF4350 network printer please look into the following steps i used it for installing 
the printer in my ubuntu 10.10 laptop 

[http://karmicdriver.blogspot.com/2010/10/setup-windows-network-printer-in-ubuntu.html](http://karmicdriver.blogspot.com/2010/10/setup-windows-network-printer-in-ubuntu.html)

Please let me know your printer type and ubuntu version, if you are facing some issue 


Best regards
avr

---

### Post by arun.in on 2010-10-27
Hi thanks man.

I have solved.. Downloaded the printer driver for ir 3300 from canon uk site. Installed the Cque inside the package by running ./setup after extracting the .tar.gz file.

Made the subnet mask and gateway address same as the remaining windows systems by editing the properties of Auto etho in network manager, the ip was also same other than the last number.

then i made a "ping" in the terminal to the printer ip and it showed success. Then clicked on the add printer button on System > Administration > Printing.

Selected the network printer and entered the ip of printer in find box. it found the printer and searched for the driver and I selected the ir3330 in the canon category. and finally the test page was printed successfully.

Thank you for your guidance. :)

---

