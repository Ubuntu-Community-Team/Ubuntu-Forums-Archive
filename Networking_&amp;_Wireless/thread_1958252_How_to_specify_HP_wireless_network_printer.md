---
title: "How to specify HP wireless network printer?"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2012-04-13
Trying to set up HP 1217nfw all-in-one wireless printer, fax, scanner.  Works on the windows machines, can't get the Ubuntu (version 10.10) box to talk to it.

I go to System>Administration>Printing and follow instructions about model number and driver etc.  Then when I get to "find printer" I choose network, type in the network address of the printer and click "find".  It comes back with some things I don't quite understand.

If the printer is on the wireless home network and the Ubuntu box is connected via ethernet cable, how do I specify the connection?  Right now it says for the connection "HP Linux Imaging and Printing (HPLIP).  If I try to print a test page, a box opens up and sez "Submitted Test Page submitted as job 193" but nothing comes out of the printer.

Any and all suggetions greatly appreciated.

---

### Post by Sef on 2012-04-14
> It comes back with some things I don't quite understand.

What does it say?

---

### Post by 23senick on 2012-04-14
Think I had similar problems, try this

 [http://ubuntuforums.org/showthread.php?t=1946888](http://ubuntuforums.org/showthread.php?t=1946888) 

You might need to install hplip, though looks like you have that already

---

### Post by agillator on 2012-04-14
I assume you are reasonably sure the printer is set up correctly. It also appears that you are using HPLIP to set up your computer. If not, that may well be the problem. If you are, make sure you have the ip of the printer, and that it is static, otherwise you would have to go through the setup procedure every time your printer is turned on. I gave a fairly detailed set of instructions for reinstalling HPLIP in another thread: [http://ubuntuforums.org/showthread.php?t=1898845](http://ubuntuforums.org/showthread.php?t=1898845), message #9. Take a look at those. You can start with the instructions for hp-setup if you don't want to completely reinstall HPLIP. A couple of caveats: select the network option, NOT the wireless option, on the first screen. If your printer is not found which it well might not be, do the manual search and search by IP. This is all simpler than it sounds and should get you going.

---

### Post by roelforg on 2012-04-14
I just clicked on the little gear in the upper right corner (the system menu)
clicked on printers
clicked on add
clicked a few times on the root element of the "Network printer" section (e.g the one with the - or the + in front of it to collapse or expand the section, i clicked on the label next to it)
it listed my hp in the "network printer" section
i click on it, give it a name, click add, password, wait 1 minute, and it printed the test page just fine and it was my default printer now.

---

### Post by raymondvillain on 2012-04-14
Thanks for all the helpful hints, still having problems.  The add printer dialog seems to be working but I can't get anything to print.  Nothing shows up in the print que.

I've selected "network printer" and after a short time it finds the printer and volunteers a connection:
 dnssd://HP%20LaserJet%20Professional%20M1217nfw%20MFP._pdl-datastream._tcp.local/

If I print a test page it says it is done, but the job never shows up in the print que.

Tried deleting and re-installing with CUPS, results were the same.  At the moment I'm re-installing HPLIP and following the instructions of agillator.

---

### Post by raymondvillain on 2012-04-14
Finally, it works!

Many thanks to all and especially agillator, whose thoughtful post did the trick. I would never have known NOT to select wireless, but instead "network" etc.

Great forum for helping confused linux uers.

I'm going to mark this solved!

---

### Post by raymondvillain on 2012-04-15
> **agillator said:**
> i assume you are reasonably sure the printer is set up correctly. It also appears that you are using hplip to set up your computer. If not, that may well be the problem. If you are, make sure you have the ip of the printer, and that it is static, otherwise you would have to go through the setup procedure every time your printer is turned on. I gave a fairly detailed set of instructions for reinstalling hplip in another thread: [http://ubuntuforums.org/showthread.php?t=1898845](http://ubuntuforums.org/showthread.php?t=1898845), message #9. Take a look at those. You can start with the instructions for hp-setup if you don't want to completely reinstall hplip. A couple of caveats: Select the network option, not the wireless option, on the first screen. If your printer is not found which it well might not be, do the manual search and search by ip. This is all simpler than it sounds and should get you going.

+1

---

