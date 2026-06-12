---
title: "Citrix XenApp Local Printing in Linux Kubuntu Lucid"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by eudemus on 2010-08-17
I had previously been able to print from Citrix ICAClient sessions using the method as follows:
[http://ubuntuforums.org/showthread.php?t=454324](http://ubuntuforums.org/showthread.php?t=454324)
[LIST]
[*]Shutdown the CUPS printing system, 
[*]edit the /etc/cups/cupsd.conf file and add "Printcap etc/printcap" to the file, somewhere near the top
[*]Restart CUPS
[/LIST]

That doesn't work for me since the upgrade to Lucid.

Instead, I've needed to use the following instructions - also mentioned in the above thread:

Edit ~/.ICAClient/wfclient.ini using a text editor and add (somewhere in the [WFClient] section):

DefaultPrinter=(here use the cups printer name for the printer you want)
DefaultPrinterDriver=Citrix Universal Driver

The cups printer name can be found various ways but one is by looking in /etc/printcap

Once you've saved the wfclient.ini file, your printer should be available in any new applications you open using Citrix.

Cheers, Eudemus

---

