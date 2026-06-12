---
title: "problem sharing hp 1400 psc printer on a windows machine"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by turtaf on 2009-12-25
Sorry for disturbing, but I'm going mad after this problem
It should probably fit better in a windows forum, but I'm sure to get better answers here.
Already googled and searched in the forum, but found no solution.

Here is the thing:

Installed a psc 1410 (scanner/printer device) on a linux machine (Ubuntu 9.10) and it works perfectly.
Installed samba to share the printer in my home lan.

I have 2 windows machines, one with vista and one with xp.

They both see the shared printer
While installing, both ask for the windows driver of the printer.
In the one with vista, psc 1400 was in the list of the available drivers and now it works great.

The problem is with the XP machine. PSC1400 driver is not available in the list. It asks for the driver CD, I put it,  but then the pc keeps asking for some hp****09.exe/inf files that are not on the cd, nor on the hard drive.

I even tried to install the local drivers before, both through the cd and downloading the installer from the hp website.

The pc keeps asking for those files.

I'm giving up.
Any advice, please???

---

### Post by Phosphoric on 2010-01-01
Hi turtaf,

I recall having a similar problem with XP but I can't remember the exact solution.

How I got over it was something like this:  Once XP finds the printer on your Ubuntu machine it will complain that the driver is wrong and offer you a selection of drivers, none of which include PSC1400.  I selected the latest PSC driver (950 I think) and the printer was then installed on XP as the default.

Here's where my memory has stopped, but I then went back in to the printer set up system and changed the driver to a PSC1400, trouble is I can't remember how?  Maybe I used the printer installation CD but somehow it found the right driver and was re-named PSC1400.

Sorry to be so vague but just to encourage you that it is easily solved.

Here's another tip for you if you get that far.  I've found that the Linux box is very slow to resolve communication to the printer when the address is in name format ( ie [http://ray_desktop/printers/PSC-1400-series](http://ray_desktop/printers/PSC-1400-series))

I set my printer up with the CUPS server by typing in "Localhost:631) in to the web browser on the Ubuntu box. Do a search for a new printer and it will find yours.  In the admin page select sharing in the server options.
Back to Windows, add new printer.
Add network printer
The printer I want is not listed (even if it is)
Select a shared printer by name
[http://192.168.1.xxx:631/printers/your](http://192.168.1.xxx:631/printers/your) printer name    xxx is your Ubuntu IP address.

You'll find this so much faster.

Cheers.

---

### Post by Methuselah on 2010-01-01
Are you sure the files are not on the drive.
Did you do a search through the whole CD?

Windows drivers typically have a .inf file but the folder the dialog opens might not be the one it is in.

BTW, what Phosphoric posted is an option as well.
I do not use SAMBA to share my linux computer's printer with windows Xp.
I just give it the Cups URL when adding the network printer.
But since you already have SABMA set up I didn't botther to mention this.

---

### Post by Phosphoric on 2010-01-01
OK, I've consulted the memory again.  Try this:

Install the printer direct to the XP box first.  Ie, run the installation CD and attach the printer at the appropriate time.  This will get the printer driver on to the XP box.

Re-attach the printer to the Ubuntu box.

Follow my previous instructions and get the printer recognised on the XP box, even if you have to use the wrong model initially.

Once installed on the XP box, go in to printers>properties>advanced>new driver.  At this drop down box you should find the PSC 1400 driver, select that and away you go.

Cheers

---

