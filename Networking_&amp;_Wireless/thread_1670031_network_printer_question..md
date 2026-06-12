---
title: "network printer question."
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by oldsoundguy on 2011-01-18
In a nutshell here it is.  I have several printers that I have hung off of a Windows box that I use as the print server (among other things) on my network.
I am contemplating installing a duplex attachment to my HP 6110xi all in one printer.  I know I will be able to utilize the feature on Windows printing, as the option is there in the set up.
HOWEVER, the HPLIP toolbox on my Linux machines does not even see ANY of the printers (yet I print to them all the time! ... 4 different HP printers alone!), so what am I missing  here?  Will I be able to duplex from Linux or not?

---

### Post by oldsoundguy on 2011-01-28
Updating,  I have installed HP Duplex units on two of my networked computers.

They will print both sides from the Windows machines (as they are plugged into those machines.

They will NOT, however print two sided from ANY of my Linux/Ubuntu machines.  they treat the print job as separate sheets.

Have made changes in Open Office and on the printer properties to no avail.

I can go to a Windows machine and access the file on the Ubuntu machine and it will print both sides.

THINK I am seriously missing something here!

---

### Post by SeijiSensei on 2011-01-29
What if you just use CUPS instead of HPLIP?  Does CUPS have a driver for the printer (most HPs are included by default)?  Does the driver support double-sided printing?

---

### Post by oldsoundguy on 2011-01-29
> **SeijiSensei said:**
> What if you just use CUPS instead of HPLIP?  Does CUPS have a driver for the printer (most HPs are included by default)?  Does the driver support double-sided printing?


same problem.  Trying to print out of OO and it does individual pages instead of two sided. (did the set up that I could see using properties under Cups.)

---

