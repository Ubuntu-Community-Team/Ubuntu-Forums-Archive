---
title: "Want to print wirelessly from Ubuntu to Windows 7"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by kihi.lind on 2010-11-07
I have a PC running Windows 7 attached to a printer.  I have a laptop running Ubuntu 10.04 LTS that wirelessly connected to the router next to the PC.  I know there's a way to run something on my laptop so it will be able to print, but I am a Linux idiot: I can't do anything with scripts.  I just need an easy way to do it.  Anyone know of a solution?

---

### Post by SeekingTruth on 2011-01-07
The simplest way, by far, is to simply use lpd to print:

On the Win7 Machine:

Make sure lpd is turned on in Windows 7. Under the "Programs and  Features" control panel click on "Turn Windows Features On and Off".  Expand "Print and Document Services" and make sure that "LPD Print  Service" is checked.


On the Ubuntu Machine:

Set up printing from Samba as usual, but do NOT use something like  "smb://PCName/PrinterName. Instead use  "lpd://IP_address_of_Win7_machine/PrinterName".

With this method you can bypass all the permissions issues that mess up printing from Ubuntu to a Win7 attached printer!

---

