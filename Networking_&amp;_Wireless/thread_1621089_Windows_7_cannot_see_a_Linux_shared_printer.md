---
title: "Windows 7 cannot see a Linux shared printer"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by williepabon on 2010-11-13
I have a Brother HL-2140 connected to a Linux box (Ubuntu 10.04 LTS) that I want to share on a Windows 7 home network (wireless). I followed all the configuration instructions as given on Ubuntu Documentation: Network Printing from WindowsXP. From the Windows 7 box I am able to see the printer in a webpage (using the URL). But when I use the same url in the Add Printer Wizard the system says that it couldn't find the printer. Any suggestions are appreciated.
wp

---

### Post by williepabon on 2010-11-15
Problem is solved! I applied the solution of a Windows 2000 user that had a similar problem connecting to a Linux box. He found out that Windows 2K won't connect to a Linux box if it was identified by its IP address directly. Instead he added a line on the windows host file (c:\winnt\system32\drivers\etc\hosts) to map the IP address with the Linux box hostname. For example:
#Example hosts entry
192.168.1.101 LinuxBoxName

I applied the same modification to the Windows 7 host file (same location) and then ran the Add printer Wizard again: Add printer | Choose network printer | Stop the scan | Choose printer isn't listed. The next dialog offers an option to select a shared printer by name. In the text box, enter the URL of your CUPS based printer, but this time using the mapped hostname, e.g.,

[http://LinuxBoxName:631/printers/printername](http://LinuxBoxName:631/printers/printername)

Then, you will get a dialog allowing you to select a windows driver for the printer. That does the trick!

---

