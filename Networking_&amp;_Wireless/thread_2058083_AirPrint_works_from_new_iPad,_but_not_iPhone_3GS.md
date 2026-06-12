---
title: "AirPrint works from new iPad, but not iPhone 3GS?"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by AlwaysLearning on 2012-09-14
Hi all,

Having a weird problem with AirPrint (IPP) on an iPhone 3GS and am hoping somebody can throw me a clue.

I know I'm overdue for an upgrade, I'm still running Ubuntu 11.04. In System/Administration/Printing I have "Server/Settings/Publish shared printers connected to this system" enabled. I have two cups-pdf:/ printers installed with default settings except for Printer Options/Output Resolution (150dpi) and Job Options/Orientation (one is Landscape 90 degrees, the other Portrait). Both of these printers have Policies/Shared enabled.

From a "new iPad" running iOS 5.1.1 (9B206) I can go to the Photos app, select a photo and go to Sharing/Print. In the Printer list I can see both printers and I can select either one and Print successfully. A file, photo.pdf appears (or gets overwritten) in /var/spool/cups-pdf/ANONYMOUS as per the /etc/cups/cups-pdf.conf settings.

Consulting the various logs, in /var/log/cups/access_log I can see:
```
192.168.2.10 - - [15/Sep/2012:12:12:46 +1000] "POST /printers/PDF-Landscape HTTP/1.1" 200 197 Validate-Job successful-ok
192.168.2.10 - - [15/Sep/2012:12:12:46 +1000] "POST /printers/PDF-Landscape HTTP/1.1" 200 42641 Print-Job successful-ok
```

In /var/log/cups/cups-pdf_log I can see:
```
Sat Sep 15 12:12:47 2012  [STATUS] PDF creation successfully finished (nobody)
```

Nothing appears in /var/log/cups/error_log.

In /var/log/cups/page_log I can see:
```
PDF-Landscape 36 guest [15/Sep/2012:12:12:46 +1000] 1 1 - 192.168.2.10 Photo iso_a4_210x297mm -
```

Now, from the iPhone 3GS also running iOS 5.1.1 (9B206) I can go to the Photos app, select a photo and go to Sharing/Print. In the Printer list I can also see both printers and I can select either one and Print. The iPhone thinks it has printed successfully, but no photo.pdf file appears (or gets overwritten) in  in /var/spool/cups-pdf/ANONYMOUS.

Nothing at all appears in /var/log/cups/access_log, /var/log/cups/cups-pdf_log, /var/log/cups/error_log nor /var/log/cups/page_log.

Is there another log, for say IPP, that I can look at to figure out what's going on?

Thanks in advance,
Anthony.

---

