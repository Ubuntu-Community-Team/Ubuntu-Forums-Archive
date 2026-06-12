---
title: "2 nd drive for Mythbuntu install?"
date: 2010-01-11
forum: Mythbuntu
---

### Post by Peterfc on 2010-01-11
Hi All

I tried Muthbuntu once before but did not have  much luck also i was very new to Ubuntu back in the days of Dapper. 

I would like to have another go at getting Mythbuntu up and running. I have a spare 250 gb hard drive as a second drive could i install Mythbuntu on that instead of the drive that normally boots my system up. My first drive has Karmic 9.10 installed and runs fine.

Would it make any difference what Video capture card i use as this machine will be taken to Portugal from the Uk when i retire in March/April this year. 

Peter

---

### Post by SiHa on 2010-01-11
The installer will give you a choice of (probably default to) installing on the second drive, or on the main boot drive (alongside, or on-top of the Karmic install). The GRUB menu will then allow you to choose which to boot. If you want to be double sure, you can tell it to put the bootloader (GRUB) on the second drive.
That way the PC will boot normally into Karmic unless you change the boot order in the BIOS.

If they are both PATA or both SATA, this should be fine. Not sure if it's still relevant with GRUB2, but GRUB has been known to get confused if there are a mix of types.

If you want belt-and-braces you could pull the Karmic drive and just put the 250G in for the install, the replace it and choose which to boot from the BIOS.

If you choose the last option, and wanted to  continue to boot off the second drive and choose Mythbuntu / Ubuntu at boot you would need to update GRUB after booting into Myth to make it aware of the Ubuntu install:> sudo update-grub should then pick up the other OS.

Can't recommend a card, although a quick Google suggests that DVB-T is available to 80% of households, so a Nova-T 500 might be a reasonable choice, as it works (almost)...out of the box with 9.10.

---

### Post by radnor on 2010-01-11
When it gets to the partition info, select the BOTTOM entry (manual).  It will figure out what drives are installed.  Select the 2nd one.  It will use the swap you have on the 1st drive.

After the install, grub will be run.  It will put the most recent install on top.  you can change this.

I've run several flavors of Linux on the same box w/o problems.  On one box I have 9.10, Mythtv FE only, Mythtv FE/BE (for testing only), Mint, etc.

---

