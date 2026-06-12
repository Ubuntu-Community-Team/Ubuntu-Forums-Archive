---
title: "To make the copier WIN network. ERROR"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by akondrat on 2010-10-05
Hi! 
To make the copier 
using XSANE, established on the computer (Client) under control of 
Windows, to execute scanning on the printer using the remote computer 
(ScanServer) under control of UBUNTU to which are connected through USB 
the scanner and the printer. 

ScanServer 
UBUNTU 10.04 (REMIX) 
SANE 1.0.20 
XSANE 0.996 
HP7650 (USB scanner) 
Xerox Phaser 3435 (USB printer) 

root@e-liss-nettop:/home/e-liss# lpstat -d -p 
system default destination: ELISS3435 
printer ELISS3435 is idle. enabled since Mon 04 Oct 2010 05:43:11 PM 
MSD 

XSANE 
Preference/Copy 
name: ELISS3435 
command: lp 
-n 

[I]Use XSANE started on ScanServer in mode COPY allows to receive demanded 
result: the page after copying is printed. 
[/I]
I try to receive similar result on Client 
WindowsVista/64 
XSANE 0.991 

Scanning is carried out successfully, but in mode COPY the error is 
deduced "[COLOR=red]Failed to open pipe for executing printercommand[/COLOR]" 

Use of other versions XSANE, name-command situations don't change 
various combinations of options XSANE. 

Please, help me.

---

