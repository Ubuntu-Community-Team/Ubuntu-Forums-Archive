---
title: "Can't Print to my Networked Xerox 8400 printer"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by DiAnah on 2009-01-15
I am a totally clueless newbie (or so I've been told), so please have mercy on my soul and help me with this frazzling problem.

Background: My new computer (came with VISTA) has been set up with Ubuntu as my default operating system and, though I have not done any special network setup action/protocol/install with my new computer (with either Ubuntu or Vista) yet, it is able to SEE the other computers and printers on the network, and I have been able to access some files from another computer on the network. But my computer has not, officially, been set up on the network yet and, thus, the other computers cannot see me. Presumably, the Xerox Phaser 8400 printer can't "see" me either.

So, my problem is that, if I try to print anything, I can see the 8400 on the drop-down Print Menu, but I can't see the 8400's printer properties AND nothing will print. Well, actually one print job took 5 hours to print one page! I've gotten the following weird printer error message from Ubuntu when I tried to print: (following is the end of the message.)

"Processing -- Remote Host Did Not Accept Data File (32)"

Do I need to set up my computer on the network to be able to print?  If I do, should I use VISTA to set up my computer on the network?

I'm dyslectic and don't speak tech very well, so I'm easily confused by tech-speak. Is there anyone out there who can...HELP!
DiAnah is online now Report Post

---

### Post by aesis05401 on 2009-01-15
There is usually software that must be installed to get a network print server and a client machine to communicate properly.  

If the printer is from a name brand manufacturer you should not have any trouble finding a driver download site by searching the model number and the word download. 

The fact that you were able to get the printer to do anything at all suggests that there is not an authentication issue, probably just a communication issue from not having the right driver installed.

---

### Post by halitech on 2009-01-23
go here and download the driver:

[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_US&Xcntry=USA&source=XOG](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_US&Xcntry=USA&source=XOG)

then extract the files somewhere.

then use the printer applet to add a printer. you will need to know the IP address of the machine (does it have an IP address or is it connected to a server and shared out?) Select the IPP connection option and use the IP address of the printer. If its connected via a print server, you will still need the driver from xerox but then use the networked option in the printer setup applet. When it asks what driver, select choose and browse to where the PPD files are extracted.

---

### Post by x3n3 on 2009-07-29
I got this problem with our Brother network printer at work. It turns out that my colleagues, who were on Windows XP, also had problems with the printer. But instead of getting an error message and a stalled print job, they got printed pages with unreadable gibberish symbols. 

We turned the printer on and off a couple times and that seems to have fixed the problem. It's possible that the unusually high temperature (30 deg. C) in our office this week has caused the problem.

---

