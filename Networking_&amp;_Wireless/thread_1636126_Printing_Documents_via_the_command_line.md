---
title: "Printing Documents via the command line"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by bemental on 2010-12-02
Quick question.

I've been trying to figure out how to send a document to print on a network printer (via IP address) from the command line (not a GUI interface).

Any suggestions?


Thanks,
Andrew

---

### Post by SeijiSensei on 2010-12-02
lpr [-P printer] filename

is the usual method.  If you don't specify a printer with -P then it uses the machine's default.

Are you trying to print from the machine to which the printer is connected, or remotely over the network?  If the latter, it needs to be the name of a printer that's configured locally in CUPS.

"man lpr" for more details.

---

### Post by bemental on 2010-12-02
> **SeijiSensei said:**
> lpr [-P printer] filename

Are you trying to print from the machine to which the printer is connected, or remotely over the network?  If the latter, it needs to be the name of a printer that's configured locally in CUPS.
.

I am trying to print to a network printer, but it is a large university network (and one of their printers).

Tips on the easiest way to go about printing to a static IP?

---

### Post by SeijiSensei on 2010-12-03
Can you set up CUPS to print to it?  You'll need to know what protocols it supports.  IPP or SMB ("Windows") printing are probably the most likely options.

If you can connect to the printer with CUPS, then you can use lpr from the command line with "-P nameofprinter" substituting the name you gave it in CUPS for "nameofprinter".

---

### Post by bemental on 2010-12-03
> **SeijiSensei said:**
> Can you set up CUPS to print to it

Let me better explain my predicament and perhaps that will change the advice given.

I'm a student at a large university and have recently discovered a hole in their system setup.  We currently have a pay-per-print system setup in our library, which I managed to get around by booting up a livecd and printing directly to the printer's IP address, bypassing the pay-per-print queue computer connected to the printer.

After notifying the IT department (who said it wasn't big enough of a problem to fix - and gave me kudos for using my brain) it lead me further to think about "ease of use" setups for booting from a live-cd.


In the end, without completely rolling my own custom livecd, I've been slowly developing the path of least resistance to perform particular tasks (i.e: printing, utilizing particular programs, etc) via livecd on networks that I may never frequent again.  I'm sold on the value of utilizing livecds for privacy and security purposes (leave not a trace) and am just trying to better the experience.

Now, if only I could figure out how to flip the RMB on the flashdrive I'm using to boot from...

---

