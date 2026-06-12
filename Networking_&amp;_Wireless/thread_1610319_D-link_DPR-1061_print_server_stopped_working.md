---
title: "D-link DPR-1061 print server stopped working"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by shaunthesheep on 2010-10-31
I am using Ubuntu 10.04. In the summer a few months back, I managed to get my ancient HP Laserjet 6L printer working via a wired D-Link-DPR 1061 print server and Netgear network switch. This was even though it was not on the print server's compatibility list. A couple of months later it stopped printing and I have not been able to get it going again since.

The print server has one parallel port (used by the 6L) and a couple of USB ports which I don't use. 

I have been going through the Ubuntu add printer wizard. The print server can connect via an IP address. I am using its device URI: lpd://ip address/dlk-portname

I have tried all 5 HP laserjet 6L drivers that come with Ubuntu without success. I have the foomatic/ljet4 [en] currently selected. When I try to print a test page nothing is printed and when I do a print self test I get this message:

CUPS SERVER ERROR
There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

By, the way I also have a Windows 7 PC and managed to get the 6L working with same print server using the XP drivers, but every so often it stops working. A reinstall gets it going again.

Any ideas anyone about what might be causing this?

---

### Post by shaunthesheep on 2010-11-01
I found the answer to my problem. For some reason or other the print server IP address had changed since the summer. I had to go to my router IP address, login and check attached devices. It was there that I discovered the altered print server IP. When I made the change to the IP in the URI, the printer sprang back to life.

---

### Post by katzelai on 2011-04-29
Do you mind telling me how you connect your ubuntu system to DPR-1061 and the attached printer at the first place? I had been working on it for weeks and still have no clue.

---

### Post by shevake on 2011-07-20
**Disable UPnP** on Advanced Lan > TCP/IP.

---

