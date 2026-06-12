---
title: "Printing from Ubuntu to Windows Vista USB Printer Causes Spooler Crash"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by gleslie07 on 2009-04-12
Before upgrading from 7.10 to 8.04, this issue did not occur.

When I try to print from my Windows Vista Computer with a USB Printer (HP OfficeJet 5510) using an Ubuntu Laptop (Xubuntu-desktop is installed, if that matters) the printer hangs.

The printer is connected via SAMBA with the correct credentials:
```
URI: smb://192.168.1.2/OfficeJet5510
```

Upon printing a document in Abiword, the document is added to the queue and the printer LCD displays "Printing.." but nothing happens.

Here is a screenshot from the Vista PC it is attached to:
[IMG]http://img9.imageshack.us/img9/8766/prt.png[/IMG]

The entry could not be deleted without first ending the spooler service and manually deleting the files.

Again, I did not have this problem with 7.10.  No errors occurred while syncing the printer.

Any ideas?

Thanks!

---

### Post by PerfectReign on 2009-06-08
I am hijacking this thead as I have the same issue.

I tried responding in this thread - [http://ubuntuforums.org/showthread.php?t=1164332](http://ubuntuforums.org/showthread.php?t=1164332) - and on LinuxQuestions but have had no success.

The printer in question is an HP Office Jet 5600.  I have printed locally from my laptop. It prints fine.

I tried printing via lpd and got a blinking light on the printer a job that started and a  stuck queue in Wintendo. (I can restart the queue by going into the command line in wintendo and typing net stop spooler / net start spooler.)

I switched over to smb as the print mechanism and get the same behavior.

Ideas?

---

