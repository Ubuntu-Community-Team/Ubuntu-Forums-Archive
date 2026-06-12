---
title: "Problems installing network printer on intrepid"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by vigneshvg on 2009-04-07
Hello,

Recently, I managed to setup my home office with a printer sever running Ubuntu 8.10, NOT server edition, on an old IBM Thinkpad T30 laptop. I've set up CUPS on the Thinkpad (the print server), and am able to see the HP OfficeJet J4580 at the following URL - [http://localhost:631](http://localhost:631).

To connect to this print server, I set up CUPS on my workstation (Dell Inspiron 520s, running Ubuntu 8.10). Through the CUPS web interface I added the network printer resulting in the following printer bring listed:

[FONT="Courier New"]Description: HP Officejet J4500 series
Location: on Gandalf
Printer Driver: HP Officejet j4500 series Foomatic/hpijs, hpijs 2.8.7 on 192.168.10.102
Printer State: idle, accepting jobs, not published.
Device URI: ipp://192.168.10.102:631/printers/HP_Officejet_J4580 [/FONT]

(192.168.10.102 is the IP address of the print server)

Everything looks fine, I can print a test page from the CUPS web interface on the workstation @ localhost:631 and through the CUPS web interface on <ip-address-of-print-server>:631.

Now here's the problem - from my workstation I can't see the network printer through any application other than the CUPS web interface. For example, when I go to System -> Administration -> Printing, I see an empty window, with most of the menu options disabled, except the option to connect to a server (Server -> Connect). 

Connecting to the print server shows me this though -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108971&stc=1&d=1239102717[/IMG]

and connecting to local host shows me this -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108970&stc=1&d=1239102647[/IMG]

However, when I try to print something from OpenOffice or Firefox, I get no printers listed. Running System -> Preferences -> Default Printer returns an error saying titled CUPS server error with the helpful little bit in there saying "The cups scheduler is not running". Also, here's what lpinfo has to say:

[FONT="Courier New"][vignesh: ~]$ lpinfo -v
lpinfo: Unable to connect to server: No such file or directory[/FONT]

Any ideas? I've reinstalled printers everywhere about 20 times... and the strange thing is that my XP laptop got the network printer and is working fine!

Thanks for your help!

Vignesh.

---

