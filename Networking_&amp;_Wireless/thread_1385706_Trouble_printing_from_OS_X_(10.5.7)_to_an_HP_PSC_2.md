---
title: "Trouble printing from OS X (10.5.7) to an HP PSC 2410 shared from Ubuntu"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by westonc on 2010-01-19
So, as the subject says, I have an HP PSC 2410 shared from a fresh Ubuntu 9.10 installation. Seems pretty likely everything's good on that side as far as the CUPS setup goes: I'm able to send documents to this printer over the network from another Ubuntu machine.

But so far, I haven't been able to find a setup where I can print to that printer from a MacBook on the same network.

I've tried setting things up using System Prefs > Print & Fax: I go into that panel, click on the + mark, select "IP", pick IPP, enter the IP of the Ubuntu box, leave the queue blank, enter the Name and location, and I think it's where the "Print Using"/driver selection is that I'm running into issues. 

If I use "Auto Select", it defaults to "Generic PostScript Printer", which I doubt the PSC 2410 is (and sure enough, if I print, the jobs don't go through). 

If I try "Select a driver to use...", there's not an option for an HP PSC 2410 or anything apparently close. This seems a little odd: I can plug the printer directly into one of our Macs and it immediately figures out the driver and I can print no problem, but that's apparently the way things work.  

So, that leaves one option: "Other", which, when selected, brings up a dialog apparently for the purpose of manually locating a driver. I've tried visiting HP's web site. They have drivers for earlier versions of OS X, but state that after 10.4, OS X should just come with the relevant drivers. 

I've also tried setting things up by interacting with the CUPS server on the Mac through a browser: I go to [http://localhost:631/](http://localhost:631/), select "Add New Printer", pick "Internet Printing Protocol (http)" for the Device selection, enter "http://<ubuntu-machine-ip>:631/printers/hp-psc-2400-series" for the Device URI, select "HP" for Make, and then on the next screen, we're back to the problem where the PSC 2400 just doesn't show up. There's an option to "provide a PPD file", which I assume would be the printer driver I can't find.  

A Google search for "HP PSC 2410 ppd Leopard" doesn't seem to yield much other than a reminder that the printer is supposed to just work out of the box on Leopard. A local search for ".ppd" or "2410" on either Mac also doesn't yield anything that looks like a relevant print driver. 

I'm totally stuck at this point. Any advice?

---

