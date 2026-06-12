---
title: "Cannot print from other computers to local printer"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by The__Virus on 2010-12-30
In Ubuntu 10.10, I have my printer, an Epson D120, shared. I can print from the computer itself, but other computers cannot print to it. Both Ubuntu and Windows machines have the printer successfully installed. They can access it, I can access CUPS from all these machines and the the job queue even reports the jobs sent from these computers. But the page count is unknown and nothing is printed, although it says the job is completed.

I'm quite desperate to get this to work. It would suck if I need to go back to Windows just because some minor thing goes wrong. I really don't understand why local prints are OK, but prints from the network are not working.

---

### Post by PatchesTheCaveman on 2010-12-30
What driver did you select for the printer?  When sharing printers using Linux and CUPS, there are 2 possible configurations.

One is to have two print queues on the server machine.  One installed with the normal driver for the Epson printer and the other with the "raw driver".  You only share queue that uses the raw driver.  You then select the driver for the Epson printer in CUPS on the other machines and install the appropriate driver in Windows.

The other solution (and more elegant IMHO) is to leave the print queue as is with the Epson driver and select the generic PostScript driver on the machines that access it.  CUPS just calls this the PostScript driver but on Windows it is called "MS Publisher Imagesetter" and is in the Generic category in the master list of printer drivers.

---

### Post by gordintoronto on 2010-12-30
I found this in another message:
"To add a printer from a Linux share, you must set the printer as sharable AND set the printer server settings to Publish, and grant any controls that are required."

---

