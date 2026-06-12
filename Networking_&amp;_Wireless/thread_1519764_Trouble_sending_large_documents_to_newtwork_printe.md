---
title: "Trouble sending large documents to newtwork printer"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by souta95 on 2010-06-28
I have a standard Desktop Ubuntu (32-bit) installation as a file and print server for my home network.

The printer is an HP OfficeJet 4315 (4300 series).

My issue is when I try to print large (i.e. >1MB) documents to the printer from a Windows 7 (Professional, 32-bit) client.  I'm not completely sure if it is a size issue, or an issue with the program I am printing from (Microsoft Streets and Trips 2009).

After clicking print in Streets and Trips the document just sits in the queue on the Windows machine, but does not show up on the server at all.  Printing from OpenOffice.org works fine, as does the Windows printer test page.  It does not matter if it is one page or multiple.  No status is given for the document, either.

Any thoughts?

Thanks in advance.

---

### Post by wyliecoyoteuk on 2010-06-28
Try changing the spool settings in the print driver>properties>advanced tab to "start printing after the last page has spooled" this will prevent time-outs when rendering large files
Also, in the ports tab , make sure that "bidirectional support" is not ticked.

---

### Post by souta95 on 2010-06-28
I got an error when I tried to change those settings.  The same error came up for both:

"Printer Settings could not be saved.  Operation could not be completed (error 0x00000057)"

I'm going to do a bit of research on my own, but I don't know if I'll find anything.

---

### Post by souta95 on 2010-06-28
after some searching I see similar problems on Windows 2000, all referencing something in teh event log, but I can't find anything in the event log about it.

---

### Post by wyliecoyoteuk on 2010-06-29
I expect that you are using the shared driver from the server.
One way around this might be to install the driver locally with the port set at LPT1, then change the port to 
//servername/printername

---

### Post by souta95 on 2010-06-29
I'll give that a shot, but there is no shared driver on the server.  I manualy specified the one that is built in to Windows 7 (after the setup wizard failed to find the driver on the server).

---

### Post by souta95 on 2010-06-29
It won't let me - it says the port already exists, though it isn't shown in the list of ports.  I'm not sure how to rename the share on the server so I can create a port of a different name.  Currently the share is "Officejet-4300-series" The port I was trying to make was "\\192.168.1.10\Officejet-4300-series" I got the same error when using the hostname of the server instead of its IP address (which is a static address).

---

### Post by souta95 on 2010-06-29
I managed to change the setting by reinstalling the printer (I right-clicked the share in Windows Explorer and chose Connect).  After changing those settigns nothing prints.  It pops up on the local queue, then disappears, and never shows up on the server's queue.

Update:

After playing with the settings on the printer some more it will no longer save the spooling settings, a similar error to the one before but with the hex code 0x00000006 instead.

---

### Post by souta95 on 2010-06-29
I gave up.

I set up the Windows machine as the print server.  I figured out how to get Linux to Print to an HP printer shared on windows.  The solution there was to delete the association of .spl files from Shockwave.

[http://ubuntuforums.org/archive/index.php/t-361978.html](http://ubuntuforums.org/archive/index.php/t-361978.html)

[http://www.linuxquestions.org/linux/answers/Hardware/Troubleshooting_printing_problems_from_SuSE_10_0_to_HP_PSC1350_shared_from_Windows](http://www.linuxquestions.org/linux/answers/Hardware/Troubleshooting_printing_problems_from_SuSE_10_0_to_HP_PSC1350_shared_from_Windows)

I'll probably migrate the file server hard drive to Windows as well so I don't have to leave two computers running.

Thanks for the suggestions, though.

---

