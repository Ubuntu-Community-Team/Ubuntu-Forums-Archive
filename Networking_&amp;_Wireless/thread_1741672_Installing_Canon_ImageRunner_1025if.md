---
title: "Installing Canon ImageRunner 1025if"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by lreyes6 on 2011-04-28
Hi, I'm having problems installing this network printer **Canon ImageRunner 1025if**, Ubuntu discover the printer and when I try to select the driver there is none for my model (image attached with the driver options).

I already search for my model at [open printing website]("http://www.openprinting.org/printers/manufacturer/Canon") and in the canon site but no luck. I'm guessing that that model evolved as other model but google couldn't tell me this either.

anyone with this printer?

thanks in advance.

---

### Post by Carysma on 2011-10-19
Hi

Where you able to setup the printer? if so can you post your solution.

Thanks

---

### Post by malkavk on 2011-11-01
I found a German version of the RPM drivers from Canon.

 Convert it to DEB with alien, works well, but only when installed on 10.x or 11.04.

 Install it in 11.10 gives some errors:
 **Idle - File / usr/lib/cups/filter/pstoufr2cpca not available: No such file or directory**

 Copy this file from older version does not solve the problem.

---

### Post by Carysma on 2011-11-05
Can you post the download link where you got the driver

thanks.

---

### Post by pdc on 2011-11-05
this looks like a serious printer

as Canon has offices in Asia, if one searches the Canon Asia website, one discovers drivers and support

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html)

The site comments

> Thank you for using the Canon UFR II/UFR II LT Printer Driver for Linux. This printer driver provides printing functions for Canon LBP/imageRUNNER ADVANCE/Color imageRUNNER/imageRUNNER/imagePRESS/MF series products operating under the CUPS (Common Unix Printing System) environment, a printing system that functions on Linux operating systems. 

---

### Post by Baldone on 2011-11-11
> **pdc said:**
> this looks like a serious printer

as Canon has offices in Asia, if one searches the Canon Asia website, one discovers drivers and support

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html)

The site comments
Hi, thanks, I did download that driver, but unfortunately it doesn't help.
When I try to install it it says Dependencies not satisfaiable: gs-esp...

---

