---
title: "network printer monitoring software"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by ratman99uk on 2008-12-17
Hi everyone

Im looking for an application that can monitor print jobs going through our network printers. I have some colour laser printers that do high volumes and would like to know info such as the number of colour pages printed compared to black & white documents. The names of jobs and quantiles printed would also be great. Any suggestions for applications?

The printers are 1x hp laserjet 3600 and 2x Oki C5650, with the addition of many more in the new year.

Thanks
Ratman99UK

---

### Post by ratman99uk on 2008-12-17
bump

---

### Post by beckols on 2008-12-18
I also need to know how to monitor usage, but I also want to know if there is a way to limit the amount of pages a user can print in a certain amount of time.  Is this possible?

---

### Post by beckols on 2008-12-29
bump

---

### Post by Paul Miller on 2009-01-03
CUPS has page logging facilities.  What I'd do is set up two separate logical printers for each color printer: one for color and one for B&W.  Have your users print to the B&W printer as the default and to the color printer if and only if color is needed.  You can then check out the page_log to determine how many pages were printed to each printer.

---

### Post by resolv_25 on 2010-06-23
Kind a old post, but I had the same problem.
With 10.04 this is working properly.
1. Here is the driver and install instructions:
[http://foo2hiperc.rkkda.com/](http://foo2hiperc.rkkda.com/)

2. Instead of gnome-cups-manager start: 
*~$ system-config-printer*
Add new printer, find appropriate  OKI driver (such as C5650), follow the instructions.
Device URL should be something as:
*socket://192.168.5.80:9100*
(or whatever is IP address  of the printer)

3. At the end,  default setting is monochrome, can be changed to color.
Printer options->Color Mode->Color.

Ink/Toner levels is working properly as well.

BTW, same driver on 8.04 did print monochrome only.
):P

---

### Post by ratman99uk on 2010-06-23
Thanks for getting back to me. I will try some time this week.
Regards
Ratman99UK

---

