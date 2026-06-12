---
title: "Windows can't access my Ubuntu printer"
date: 2011-10-01
forum: Networking &amp; Wireless
---

### Post by cpeachey on 2011-10-01
I have followed the instructions here.....
[http://gain4you.net/info/309/how-to-share-printer-over-ubuntu-network/](http://gain4you.net/info/309/how-to-share-printer-over-ubuntu-network/)

The printer is attached to my Ubuntu 11.04 desktop. I have pasted the url into the windows browser and it shows the name of the printer.
[http://192.168.1.2:/printers/](http://192.168.1.2:/printers/)
(I can also access CUPS from the XP machine with a similar url)
When I "add printer" using the XP windows I get the message ...
"Windows cannot connect to the printer. Either the name is wrong or the printer has lost it's connection to the server"

Any suggestions please?
Chris

---

### Post by drdos2006 on 2011-10-01
Originally Posted by hidesertmlb in the Server Section

1- in /etc/samba/smb.conf ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

regards

---

### Post by cpeachey on 2011-10-01
Tried the above but still have the same result.
Chris

---

### Post by drdos2006 on 2011-10-01
The format for the URL for Windows network printer is :--

http://<ip-address-of-printer-host>:631/printers/<name-of-printer>

regards

---

### Post by cpeachey on 2011-10-02
Thanks for your help. I am now printing from WinXP to the Printer on the Ubuntu machine.
Chris

---

