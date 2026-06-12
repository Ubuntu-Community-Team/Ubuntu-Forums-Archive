---
title: "Connect to Network Printer wirelessly not working?"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2010-01-06
Here's the setup:

Brother DCP-540CN Network Printer, connected to wireless router via a network cable.

This works seamlessly with all computers connected to the LAN via wires, using Windows or Xubuntu 9.10.

Just setup a new PC with Xubuntu 9.10, running off the wireless side of the router, can see and access other PCs on the LAN, and have internet access, and installed the usual Brother drivers for the printer from the repos, and the scanner drivers from Brother.

Cups (localhost:631) found "three" Brother DCP-540CN printers (each with a different connection setting). Cups was happy to set up each of these (I tried one at a time)

None will actually print anything.

Similarly with the scanner. Installs fine and running the config shows that a scanner is installed.

But xsane cannot find the scanner.

Tried a reboot but with the same outcomes.

Yet to try setting up with a wired connection first, and then see if it follows through when going back to wireless, but is there something I am missing?

---

### Post by Jose Catre-Vandis on 2010-01-06
OK, self solved again, but helped by other posts on the forum regarding Brother printers on Karmic (more regressions from Karmic/Brother - grrr!)

Started off with the PC connected with ethernet cable (have not tested just doing it wirelessly, but guess it might work just the same)

Switched off the Printer !  (we were having to do this back in Edgy!)

Installed all the printer drivers, including the brscan2 scanner driver
(I had removed all of these prior to commencing)

**Printer**

Went to System -> Printing and clicked on the Add Printer icon
Expanded the Network Printer item in list on the left
Selected Brother DCP-540CN (10.10.10.80) - (the IP of **my** printer)
This provided the device URI of **socket://10.10.10.80:9100**
Then selected the correct driver: **Brother DCP-540CN CUPS v1.1**, from the list
Clicked OK
Printed Test Page
**[COLOR="SandyBrown"]Success[/COLOR]**

**Scanner**

Ran the config line as sudo:
**sudo brsaneconfig2 -a name=BrotherScanner model=DCP-540CN ip=10.10.10.80**
(note I used sudo this time around)
Checked with
**brsaneconfig -q**
Ran xsane
Unlike with Jaunty, no choice of devices, but the scanning for devices dialog pops up, disappears then xsane starts up, showing Brother DCP-540CN
Test Scan
**[COLOR="SandyBrown"]Success[/COLOR]**

**Go Wireless**

Shut down PC, remove ethernet cable, and boot up again as wireless
Retest Printer and Scanner
**[COLOR="SandyBrown"]Success[/COLOR]**

Oh well :)

---

### Post by gandalf2000 on 2010-02-10
A big thank you to you, Jose.  I finally got my printer working again.

---

