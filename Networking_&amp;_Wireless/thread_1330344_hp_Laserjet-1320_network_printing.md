---
title: "hp Laserjet-1320 network printing"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by peter.h on 2009-11-18
Hi,

I am having problems printing on an hp Laserjet-1320 network printer from my ubuntu 9.10 machine.  I can find the printer in the network (listed in the Networking Printer list) and have tried both  connection configurations 'HP Linux Imaging and Printing (HPLIP)' and 'APPSocket/HP JetDirect'·

When print the print job just sits in the job queue with status 'processing'.

I have been able to print using another machines (ubuntu 9.04) selecting it as a CUPS server (Server>>Connect: CUPS Server = host ip).  

Thanks in advance for any replys

---

### Post by Ben McKay on 2009-12-02
Same problem, but not a network printer, just plugged in to my desktop by a USB connector.

---

### Post by yavoh on 2009-12-12
Same here! With a USB 1320.  Sometimes it leaves the job queue but the green light still blinks on my printer and nothing prints.  Test pages print correctly, but not PDFs.  Other filetypes are iffy.

---

### Post by frnc on 2010-01-21
Did anybody find a clue in the meanwhile? I have the same problems: hp 1320 connected via USB port (no network), Karmic recognizes the printer, configures it, I can see it in the printers panel under the administration menu. 

When I enter CUPS manager I can successfully print a demo page, but when I try to print a pdf file it just doesn't work, although the green light blinks for a couple of seconds and a job marked as completed can be seen in CUPS's job administration **page.

No idea what to do, any help appreciated.

---

### Post by emgee3 on 2010-01-30
Looks like I have the identical problem to the OP. 

My HP LaserJet 1320tn is automatically detected as a network printer, but no matter which settings I pick for it, the job just says processing and never comes out. No leads from looking through the log files.

---

### Post by pastudan on 2010-02-05
I have the same problem. Happens often with PDFs, but that's all I've been printing.

This issue is interesting though,because when I had it connected to a networked server running 9.04 it was running flawlessly, but now that I've moved it over to my desktop with 9.10 it hasn't worked right since.

Seems to me that an updated driver is causing problems. I'll post if I can find a workaround as rolling back the driver doesn't sound too hard :-/

---

### Post by pastudan on 2010-02-06
After about a week of getting frustrated with this printer I seem to have found a solution that has been working so far...

For me, this printer was added by default as soon as I plug it into USB. So we just need to change the driver it uses by default...

1) System -> Administration -> Printing
2) Right click your HP LaserJet1320 -> Properties
3) Make and Model -> Change...
4) Select printer from database -> HP -> Forward -> LaserJet 1320 -> HP Laserjet 1320 hpijs ***OR*** HP LaserJet 1320, hpcups -> Use the new PPD as is.
5) Close out and test a PDF.

This worked for me.

Notes: My 32 bit netbook gave me different options for drivers than my 64 bit desktop did (hpijs vs hpcups respectively), but regardless, it sounds like changing the driver from the default Postscript option seems to make a difference.

I'd like to know if anyone has any success with this method. I'd really like to file a bug with Ubuntu, but I'm not sure where.. Postscript driver perhaps?

---

### Post by Alex_Koekie on 2010-02-16
Hello,

Just posting my experience as it might be helpful to someone. (ubuntu 9.10 karmic linux 2.6.31.19)

I've had a similar problem with my HP Laserjet 4 Jetdirect printer.
It dit setup nice and printed a testpage as well, but no large 4mb pdf files. Those files just stayed in the waitinglist even if i did reset the printer and pc. But when i reset the pc and printer and tryed a small txt file or pdf 100kb it worked fine.

Strange enough changing my pdf viewer from the standard document viewer to Okular PDF viewer fixed the problem. (didn't try any other viewers, this was the first attempt) I can now print large and small pdf files. So there seems to be an incompatibility when the standard ubuntu document viewer encounters a large pdf file and a jetdirectcard.

Greeting,
Alex_Koekie

---

### Post by Gixxy on 2010-02-20
Same issue here with a 1320n. The hcups drivers did not help. Suppose I shall mess with it some more.

---

### Post by tombott on 2010-09-15
I get the same problem printing to the following HP Models:

HP LaserJet 4000
HP LaserJet 4100
HP LaserJet 4250
HP LaserJet P4105

I'm installing Adobe Reader at the moment to see if it makes any difference printing via that.
I've tried opening the PDF's into GIMP  but that won't print either.

All of the printers I have tried printing to have been via JetDirect.

---

