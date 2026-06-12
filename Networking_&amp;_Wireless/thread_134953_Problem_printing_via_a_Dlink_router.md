---
title: "Problem printing via a Dlink router"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by kboutin on 2006-02-22
I have been searching the forums for some answers
but even though I got close to a solution I am still stalled.

[http://www.ubuntuforums.org/showthread.php?t=32692](http://www.ubuntuforums.org/showthread.php?t=32692)
[http://www.ubuntuforums.org/showthread.php?p=257891](http://www.ubuntuforums.org/showthread.php?p=257891)

I have breezy 5.10 installed on my Thinkpad A21m fine.
I am trying to configure my printer to work via a Dlink DI-713p
which is a good old router/AP with an embedded print server.
The printer is an hp LaserJet 1100 connected to the router
by a nice long and thick parallel cable.

When I try to follow the straight route described in both 
posts above:

1) System > Administration > Printing. 
2) Add a printer
3) Network Printer > Unix Printer (LPD) 
4) Host: 192.168.0.1
5) Queue: lp 

Then when I click forward to chose the driver, my system freezes.
The hard disk starts scratching like crazy but the system never comes back. I have to do a hard shutdown :( 
This behaviour looks like a bug to me. Should I report it somewhere?

I was able to print directly to the 1100 from the laptop with the driver supplied
for the HP in breezy badger. 

The printserver configuration with the D-link has been working (wired and wireless)
for months with both of our Laptops running XP (Thinkpad and HP)

Earlier last week I followed a forum thread that I cannot find anymore that
hinted about the freeze I am describing. The only way out apparently was
to edit the cups.conf file. With that approach I was able to get to the printer
via the router but the test page sent postscript-3 to the poor old 1100 that
choked on this stuff. The 1100 is a cheap Windows only printer I think.

Anybody can help here or point me other thread that could help

---

### Post by jamesr on 2006-02-24
I have a similar problem but with a GVC router but I cannot get to print at all so I would very curious about the steps that you took. I have had many funnies with Kubuntu system and adding the printer. Did you setup by cups and the web interface or not ? or just by gnome

---

### Post by kboutin on 2006-02-24
James,

I found the thread  I was referring to last night:
[http://www.ubuntuforums.org/showthread.php?t=30288](http://www.ubuntuforums.org/showthread.php?t=30288)

Since the GNOME printing utility was causing a system freeze 
I reverted to editing the cups.conf and printers.conf file
exactly as described in the post #3 of the thread
[http://www.ubuntuforums.org/showthread.php?p=158787#post158787](http://www.ubuntuforums.org/showthread.php?p=158787#post158787)
I think this guy is experiencing the same behaviour we are seeing.

My Ubuntu laptop see and talk to the laserjet 1100 via the Dlink router but the test page sent is a PS-3 and my hp is a PCL5 only printer.
I know the driver exist for this machine since I printed directly from the
LPT port. I just need to configure it properly far the UNIX networked
printing mode.

I'll try other tricks tonight and report on my findings.

p.s. Canadian women are doing great at Turin :D

---

### Post by jamesr on 2006-02-24
not like the mens hockey team but that's  you get when the team does not show up for work

---

### Post by kboutin on 2006-02-24
James,

Do you also get the *freezing* of your system while trying to configure printing with the GUI? Looking at the configuration of your machine it occurred to me that we are both running close to the limit suggested for RAM (128 MB).

---

### Post by wilksch on 2007-08-27
I found this post while searching for a solution to a similar problem trying to print to a HP LaserJet 4L via a D-Link DI-713P print server under Ubuntu 7.04 (Feisty Fawn).

As with the original poster, I would try to add the printer in the following way:
1) System > Administration > Printing
2) Add a printer
3) Network Printer > Unix Printer (LPD)
4) Host: 192.168.0.1
5) Queue: lp 
...only to have the "Add a Printer" GUI lock-up when I clicked "Forward" after entering the Queue. However, I was able to close the locked dialog window by clicking the [X] in the top-right corner, waiting a few seconds, and selecting "Force Quit" when prompted.

Some other posts suggested adding the print server IP address (192.168.0.1) to /etc/cups/cupsd.conf and restarting CUPS, but this did not help.
  eg. add "Allow 192.168.0.1" under the <Location /> section, then run "sudo /etc/init.d/cupsys restart"

I was finally successful when adding the printer using the CUPS admin interface:
1. Browse to [http://localhost:631/](http://localhost:631/)
2. Add printer
3. Name:  LaserJet4L
4. Device:  LPD/LPR Host or Printer
5. Device URI:  lpd://192.168.0.1/lp
6. Make/Manufacturer:  HP
7. Model/Driver:  HP LaserJet 4L - CUPS+Gutenprint v5.0.0.99.1 (en)
8. Popup prompts me to Enter username and password for "CUPS" at [http://localhost:631/](http://localhost:631/)

At this point I had to enter MY OWN username and password, not root's. For some reason, when I used root's username/password I received a "401 Unauthorized" error (I picked this tip up from [http://forums.linux-foundation.org/read.php?24,625](http://forums.linux-foundation.org/read.php?24,625)).

That's it! The printer was added successfully and is available for myself and and other Ubuntu users on my host.

---

### Post by mfdc1969 on 2007-09-16
I have a DI-704UP and my recent attempt (as per the post of wilksch 2 Weeks Ago 07:32 PM) was successful due to the info on this post.

An extra step that I took *before* clicking on the button to add a new printer was go to Global Settings and enable the option **Detect LAN Printers** which opened port 631. Prior to that all previous attempts were very unsuccessful. 

Thanks everybody!

- Mike

---

