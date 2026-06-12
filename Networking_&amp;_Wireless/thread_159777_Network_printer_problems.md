---
title: "Network printer problems"
date: 2006-04-13
forum: Networking &amp; Wireless
---

### Post by chloraldo on 2006-04-13
I am using a brother printer (MFC-620CN). I have drivers and everything to print over USB. But it's a network printer and I would like to use it over the network.

It's IP-Adress is 192.168.1.036

When editing the printer properties I'm not sure what to chose (IPP? URL?)...

I tried using "System > Administration > Printing" an "http://localhost:631"

Here's what I get in [http://localhost:631](http://localhost:631)...

```
Description: MFC-620CN
Location:
Printer State: idle, accepting jobs.
"Network host '192.168.1.036' is busy; will retry in 30 seconds..."
Device URI: [http://192.168.1.36:80/](http://192.168.1.36:80/)
```

Any help?

Thanks!

---

### Post by 3space on 2006-04-13
Chloraldo,

In case our problems are similar, here's what's going on with me...

I can ping my printer from terminal or network tools, 100% success
Used printer setup wizard
Selected connection type: HP JetDirect
Chose HP4500 printer driver (not from disk, only from list - is that correct?)
Tried PostScript and PCL-6 protocols
Send jobs to printer, get same message as you:
   Printing: Network host '192.168.1.101' is busy; will retry in 30 seconds...

Printer: HP Color LaserJet 4500N
Accessories: HP JetDirect Card
IP Address of Printer: 192.168.1.101
Port: 9100
Connected directly to 4-port 802.11G Wireless Router

Settings above are those used by my 4 XP machines.
Currently running Ubuntu 5.10 off LiveCD (all settings stored in virtual memory)

Does anybody have any ideas?  Am I supposed to download the driver from somewhere, or when it's in the list does that mean that it should work?

I have two issues holding me back from a full install.  This one, and difficulty figuring out PocketPC (Windows Mobile 5.0) syncronization.

Thx.

---

### Post by Aniquibobo on 2006-04-14
Hi

I have also problem with my Konica Minolta Magicolor 5430DL.
(I have this file:magicolor5430DL-1.7.1.tar.gz 	357 KB 	03/27/2006)
I got my printer on "setup list", i can ping my printer but i can't print.
I wonder if i have to move back to Win  to be able to print...?:-k 
Sounds crazy...](*,) 

Ubuntu looks nice , but i have to be able to use my printer.
Looks like that it is several people with "printer" problems. Anyone good on this ?

Many thanks....

---

### Post by nomad111 on 2006-10-31
try lpd://<ip-address-of your printer>/BRN_738DE8
as the printers address (URI)

by default the mfc-620cn's queue name is BRN_738DE8 you can confirm this by checking the LAN settings on ur printer.

---

### Post by trevoz on 2006-11-03
> **nomad111 said:**
> try lpd://<ip-address-of your printer>/BRN_738DE8
as the printers address (URI)

by default the mfc-620cn's queue name is BRN_738DE8 you can confirm this by checking the LAN settings on ur printer.

This may be true for your 620CN, but it's unlikely to be true for anyone else's. You see the queue name is the string BRN_ followed by the last 6 digits of the printer's MAC address :)

---

### Post by Ouaisne on 2007-01-07
I am also looking for help setting up my printer although as I have only just installed Linux for the first time (24 hours ago) you may have to keep things a bit simple.

Printer: Xerox Phaser 6100DN
Port: 9100 shows on documentation as does 631
Network path (from printer): [http://192.168.0.3:631](http://192.168.0.3:631)
Connected directly to Netgear 4-port 802.11G Wireless Router
This computer also connected directly (not wireless)
Router always gives printer same IP address,

I have been able to access the internet from first install and can view my network hard drive.

I have tried various settings, can't find the answer in any other thread and wonder if anyone can come up with a definitive (simple) solution.

TIA

---

